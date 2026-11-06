https://arxiv.org/pdf/2611.02053

|Level|Question|
|---|---|
|**Look**|Which region of the image is available to me?|
|**Perceive**|What objects are in that region?|
|**Understand**|What can I infer from those objects?|

## Central question

Before asking whether a VLM understands an image, can it identify what visual input it actually received?

## Same wrong answer, different failures

Imagine a dog on grass, with the question “What animal is grazing?” A model answering “sheep” might have:

- **Perceive failure:** Used the image but mistaken the dog for a sheep.
- **Look failure:** Followed the wording’s association with sheep without relying on the image.

Source: paper introduction, Section 2, and Figure 2. Explanation added by Codex at the researcher's request.


