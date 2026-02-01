# Project: Academic Paper Analyzer

Assignment spec/prompt for Claude Code to help scaffold the assignment.

## Overview

Build a LangGraph pipeline that takes a DOI or arXiv URL as input and produces a summary of the paper. The pipeline should gracefully handle cases where full text is not accessible by falling back to an abstract-only summary.

## Input

A single string: either a DOI (e.g., `10.48550/arXiv.1706.03762`) or an arXiv URL (e.g., `https://arxiv.org/abs/1706.03762`).

## Output Format

JSON with the following structure:

```json
{
  "title": "Paper title",
  "authors": ["Author 1", "Author 2"],
  "doi_link": "https://doi.org/10.xxx",
  "published_doi_link": "https://doi.org/10.yyy" or null,
  "open_access_link": "https://..." or null,
  "full_text_available": true/false,
  "citation_count": 12345 or null,
  "venue": "NeurIPS 2017" or null,
  "summary": "# Paper Title\n\n**Authors:** ...\n\n## Summary\n\n...\n\n## Impact\n\nCitations: 12345 | Venue: NeurIPS 2017\n\n## Links\n\n- [DOI](...)\n- [Published Version](...)\n- [Open Access PDF](...)"
}
```

The `summary` field contains a self-contained markdown document including title, authors, summary text, impact metrics, and links. The `full_text_available` boolean indicates whether the summary was generated from full text or abstract only. The `published_doi_link` field contains the DOI of the final published version if the input was a preprint and a published version exists. Note that DOIs can point to preprints too (e.g., `10.48550/arXiv.1706.03762` for arXiv, `10.1101/...` for bioRxiv), not just published papers.

## Pipeline Flow

1. **Parse input** — Determine if DOI or arXiv, normalize the identifier
2. **Fetch metadata** — Call CrossRef API (for DOI) or arXiv API to get title, authors, abstract
3. **Look up impact** — Call Semantic Scholar API to get citation count, venue, and published DOI (if input was a preprint, regardless of whether it was provided as URL or DOI)
4. **Find full text** — If DOI, search Unpaywall for open access PDF; if arXiv, construct direct PDF link
5. **Conditional routing:**
   - If full text URL found → fetch content, analyze, generate full summary
   - If not found → generate limited summary from abstract only
6. **Return JSON** with structured data, impact metrics, and markdown summary

## Technical Requirements

- Use LangGraph with a custom `TypedDict` state
- Use `@tool` decorator for API calls (metadata lookup, Semantic Scholar impact lookup, Unpaywall search)
- Use `add_conditional_edges` for the full-text-found vs not-found routing
- Use Typer for CLI interface accepting a DOI or URL argument
- Handle common error cases gracefully (invalid input, API failures, missing data)

## APIs

- **CrossRef** (`api.crossref.org`) — metadata for DOIs, free, no auth required
- **arXiv API** (`export.arxiv.org/api`) — metadata for arXiv papers, free
- **Semantic Scholar** (`api.semanticscholar.org`) — citation count, venue, and published DOI lookup. Two options: (1) unauthenticated access with shared rate limit pool, or (2) request a free API key with your .edu email for a dedicated rate limit
- **Unpaywall** (`api.unpaywall.org`) — open access lookup, free tier requires email as identifier

## State Schema (suggested)

```python
class PaperState(TypedDict):
    input_url: str                # Original DOI or arXiv URL
    input_type: str | None        # "doi" or "arxiv"
    identifier: str | None        # Normalized DOI or arXiv ID
    metadata: dict | None         # title, authors, abstract, etc.
    impact: dict | None           # citation_count, venue, published_doi (from Semantic Scholar)
    full_text_url: str | None     # Open access link if found
    full_text: str | None         # Extracted content if fetched
    summary: str | None           # Final markdown summary
```

## Potential Failure Points

Students should handle these gracefully:

**Input parsing:**
- DOI format variations (`10.xxx/yyy`, `doi:10.xxx`, `https://doi.org/10.xxx`)
- Preprint DOIs (`10.48550/arXiv.xxx` for arXiv, `10.1101/...` for bioRxiv/medRxiv)
- arXiv format variations (`arxiv.org/abs/`, `arxiv.org/pdf/`, just the ID)
- Invalid/non-existent identifiers

**API issues:**
- Rate limits (CrossRef, arXiv, Semantic Scholar, Unpaywall)
- API downtime or timeouts
- Missing fields in responses
- Semantic Scholar may not have data for very new or obscure papers

**Content access:**
- Unpaywall finds nothing (paywalled everywhere)
- Open access link is dead/broken
- PDF is scanned images (no extractable text)

**PDF extraction:**
- Complex layouts (multi-column, tables, equations)
