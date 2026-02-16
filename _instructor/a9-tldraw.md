# A9 — TL;Draw

## Concept

Students receive a working app that takes a document and displays a summary and an SVG. The app uses mock LLM calls and a hardcoded SVG. Students progressively replace the mocks with real functionality, add new nodes, implement conditional routing, and extend the Streamlit interface.

The assignment is the basis for Code Review 2.

## What the starter provides

- A functional Streamlit app they can run immediately
- A simplified LangGraph workflow with two nodes:
  - `summarize` — returns a hardcoded summary (mock)
  - `generate_svg` — returns a hardcoded SVG through an SVG validation/sanitization helper
- A custom state (`TypedDict`) with fields for the full pipeline (document, summary, visual_prompt, svg_code, image, output_mode, etc.) — more fields than the starter graph uses
- Additional code present but not wired into the graph (nano banana image generation, visual prompt generation logic)
- The Streamlit interface displays the document input area, the summary, and the rendered SVG — but has no output mode toggle yet

## What students build

### Phase 1: Real LLM calls
- Replace the mock `summarize` node with a real LLM call
- Replace the mock `generate_svg` node with a real LLM call that generates SVG code (the validation helper stays in place)

### Phase 2: Visual prompt node
- Add a `generate_visual_prompt` node between summarize and generate_svg
- This node takes the summary and generates a descriptive prompt for the visual output (used by both the SVG and image paths)

### Phase 3: Conditional routing and nano banana
- Wire in the pre-built image generation code (nano banana API call)
- Add a `generate_image` node
- Implement conditional routing (`add_conditional_edges`) after `generate_visual_prompt` — routes to `generate_svg` or `generate_image` based on user selection
- Add the output mode toggle to the Streamlit interface
- Display the image result when the image path is selected

### Optional: Interface enhancements
- Additional changes to the Streamlit interface — styling, layout improvements, interactive elements, or display enhancements

## Skills tested

- Custom state beyond `MessagesState` (A7)
- Multi-node LangGraph workflow (A7)
- `add_conditional_edges` for routing (A7)
- Streamlit interface integration and modification (A8)
- Reading and integrating existing code they didn't write
- Prompt engineering (getting usable SVGs from an LLM)

## Graph evolution

```
Starter:     document → summarize → generate_svg → display

Final:       document → summarize → generate_visual_prompt → [conditional] → generate_svg   → display
                                                            └─────────────→ generate_image  → display
```

## Design decisions

- **Start functional, add features:** Students run the app before writing any code. Each phase produces a working app.
- **Pre-built unused code:** The image generation code exists from the start but isn't wired in. Students read it, understand it, and integrate it. This mirrors real-world development.
- **SVG validation helper:** Pre-built in the starter's `generate_svg` node. Catches broken SVG output from the LLM so students can focus on prompt engineering rather than debugging XML.
- **Progressive complexity:** Linear graph → add a node → add a branch. Each step is independently testable.
