---

# Context Windows as Bandwidth: Compressed Retrieval Keys for Efficient Knowledge Access in Language Models

**Joshua Archer** · May 2026

## Abstract

Large language models are commonly treated as memory-limited systems. In practice, their primary constraint is bandwidth: only a fixed amount of information can be actively processed within the context window at inference time. This paper proposes compressed mnemonic keys as an alternative to retrieval-augmented generation (RAG) — short token sequences that encode retrieval paths rather than document content, allowing the same context budget to cover an order of magnitude more knowledge.

## Paper

📄 [context_windows_as_bandwidth_neural_trunk_paper.pdf](./context_windows_as_bandwidth_neural_trunk_paper.pdf)

## Key Findings

- Compressed keys achieve comparable or superior retrieval accuracy to RAG while reducing token consumption by approximately **1.9×** in testing (approaching **10×** in production configurations)
- Keys win **57% of head-to-head** comparisons vs. RAG across 30 queries
- Higher precision when on target: average rank **1.18** vs. **1.63** for RAG
- **0.90 cosine similarity** across semantically equivalent rephrasings — robust to phrasing variation
- Keys and RAG operate as complementary profiles: keys are sharp and cheap for known domains; RAG is broader for exploratory queries

## The Core Idea

The context window is not a memory container — it is a constrained communication channel. Standard RAG spends that bandwidth on raw document text optimized for human readers. This paper proposes spending it on compressed pointers instead: mnemonic keys that encode the *access structure* to knowledge rather than the knowledge itself.

A 40,000-token trunk allocation carries ~2,000 keys. The same allocation in RAG carries 80–200 document chunks. With hierarchical key-to-key indirection, the theoretical reachable knowledge approaches 5 billion nodes.

## Experimental Infrastructure

Evaluation was conducted on a live system:
- **Vector store:** Qdrant on Mac Mini M4 Pro, 1,691 curated knowledge points across four semantic collections
- **Embedding model:** Ollama serving `nomic-embed-text` (768-dimensional)
- **No proprietary models or APIs required**

## Files

| File | Description |
|---|---|
| `context_windows_as_bandwidth_neural_trunk_paper.pdf` | Full paper (12 pages) |
| `main.tex` | LaTeX source |
| `diagram_trunk_final.png` | Trunk architecture diagram |
| `diagram_rag_vs_keys_elite_final.png` | RAG vs. keys pipeline comparison |
| `diagram_indirection_final.png` | Hierarchical indirection diagram |

## Citation

```
Archer, J. (2026). Context Windows as Bandwidth: Compressed Retrieval Keys for 
Efficient Knowledge Access in Language Models. 
https://github.com/joshuaarcher/context-windows-as-bandwidth
```

## License

[Creative Commons Attribution 4.0 International](./LICENSE) (CC BY 4.0)

---

*This work was developed in collaboration with the Pequeno multi-agent AI system. The system's contributions to ideation, articulation, and refinement are acknowledged with gratitude.*

---