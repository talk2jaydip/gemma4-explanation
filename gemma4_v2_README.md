# Gemma 4 handwritten architecture package v2 - extended

This package is the "handwritten whiteboard" explainer for the Gemma 4 architecture, delivered in four complementary forms. All of them share the same handwritten SVG style and the same source list.

## What's in the box

### Long-read article
- `gemma4_architecture_handwritten_substack_v2.html` - single-file standalone article, 17 illustrated steps, animated inline SVG diagrams, per-step worked calculations. Opens in any browser with no build.
- `gemma4_architecture_substack_embed.html` - same article with every diagram fully inlined (no external `<object>` tags) and without the site chrome. Paste this into a Substack "custom HTML" block.

### Jupyter notebook companion
- `gemma4_architecture_explainer_notebook_v2.ipynb` - 51 cells. Mirrors the article's structure with runnable Python: model-family table, dense-vs-MoE active-parameter math, full-vs-sliding attention score growth, GQA KV savings, 31B layer pattern, PLE variance check, quantization table, audio token budget, prefill-vs-decode cost plot, vision token budget, function-calling turn, and model decision tree.

### Reusable diagram assets
- `gemma4_assets_v2/` - 15 editable SVG diagrams + PNG exports under `png/`. Use these in slides, internal docs, or other blog platforms.

### Netlify-ready static site
- `site/` - deployable multi-page site (home, article, notebook, assets, about, 404). Contains `netlify.toml`. To deploy: drag the `site/` folder onto Netlify, or run `netlify deploy --dir=site` from the CLI.

## All 15 diagrams

1. architecture_overview - one-screen mental model (text / image / audio -> decoder stack -> logits)
2. tokenization_flow - raw string -> SentencePiece 262K -> ids -> embedding
3. decoder_block - residual stream with norms + attention + MLP/MoE
4. hybrid_attention - sliding local vs global arcs
5. gqa_heads - 32 Q heads sharing 16 or 4 KV heads
6. layer_pattern_strip - 60-layer 5:1 rhythm
7. kv_cache_math - naive full vs hybrid estimate
8. rope_rotation - content vector rotating by position
9. vision_token_budget - 960x672 patches -> 3x3 pool -> 280 tokens
10. audio_encoder - waveform -> mel -> encoder -> merged sequence
11. moe_router - 128 experts, top-8 + shared
12. ple_detail - token-identity + context-aware projection, scaled by 1/sqrt(2)
13. quantization_memory - BF16 / SFP8 / Q4 bars across the family
14. inference_pipeline - prefill vs decode, KV cache growth
15. function_calling_loop - schema -> decode -> call -> observation -> continue
16. decision_tree - which Gemma 4 for which job

## Sources

Full citation list with live links: `site/about.html` or the "Endnotes and source anchors" section at the end of the article HTML. Primary sources: Google Gemma 4 model card, Gemma vision docs, Hugging Face Transformers Gemma 4 docs, public 31B config.json, Keras Hub Gemma4Backbone, Google Developers Blog, and the foundational Transformer / RoPE / GQA / MoE papers.
