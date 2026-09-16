# Chapter 9: Building and Sharing Demos

*Estimated study time: ~2-3 hours*

Covers **Gradio**, the library (also owned by Hugging Face) for wrapping a model in a shareable web UI in a few lines of Python.

```python
import gradio as gr
from transformers import pipeline

classifier = pipeline("sentiment-analysis")

demo = gr.Interface(fn=lambda x: classifier(x)[0], inputs="text", outputs="label")
demo.launch()
```

Demos can be deployed for free on **Hugging Face Spaces**, which gives a public URL that anyone (including recruiters or teammates) can open without any setup on their end.

---
[← Chapter 8](chapter-08-how-to-ask-for-help.md) | [Back to index](README.md) | [Next: Chapter 10 →](chapter-10-curate-datasets.md)
