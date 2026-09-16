# Chapter 5: The 🤗 Datasets Library

*Estimated study time: ~4-5 hours*

## Loading data from anywhere

`datasets.load_dataset()` reads from the Hub, but also from local CSV, JSON, text, and pandas sources directly, which makes it a general-purpose data-loading layer rather than a Hub-only tool.

## Slicing and processing

- `.map()`, `.filter()`, `.sort()`, `.shuffle()`, `.train_test_split()` all mirror pandas-style operations but stay lazy and memory-mapped.
- `set_format("pandas")` or `set_format("torch")` changes how rows are returned without copying the underlying data.

## Big data — when it doesn't fit in RAM

Datasets are backed by Apache Arrow and memory-mapped from disk, so a dataset can be far larger than available RAM and still be processed in streaming fashion (`load_dataset(..., streaming=True)`) without ever loading it fully into memory.

## Semantic search with FAISS

The chapter builds a simple semantic search engine: embed a corpus of text with a sentence-embedding model, add a FAISS index to the dataset with `dataset.add_faiss_index()`, and then query it with `dataset.get_nearest_examples()` to retrieve the most similar rows to a query embedding.

---
[← Chapter 4](chapter-04-sharing-models.md) | [Back to index](README.md) | [Next: Chapter 6 →](chapter-06-tokenizers-library.md)
