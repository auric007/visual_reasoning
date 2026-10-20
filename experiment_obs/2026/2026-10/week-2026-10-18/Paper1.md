[[s41746-026-02676-5.pdf]]
Key concept learning for medical vision language model with reasoning capabilities


TODO: The VLM i trained, how exactly the all the section VLM generating, it is token by token or after producing a section lets say visual_grounding, it is looking at the visual token again or it is generating all token simultneously

Things to take care of:
- Just ordinary training, trains the model to reproduce the whole sentences.


	**Reasoning is a claim to examine.** Better answers and detailed explanations do not, by themselves, establish that the model reasons faithfully from visual evidence. 
	I want to know how, better explanation is conditioned on visual signature. if model is giving better signature thats mean it is looking at the images



TODO: Our method supervises output tokens. Whether that produces better use of visual evidence is an empirical question we should keep open. I need to check this on my all trained VLM, is visual evidence is influencing the produced token or just it is there. 


gap: Emphasizing military words during training does not automatically teach the model where to look in an image.

The three component that they build:
1. Dataset: domain QA dataset
2. key concept dictionary: This dictionary collects domain terms from the training answers.
3. Selective loss computation: ConceptVLM selectively includes positions associated with dictionary concepts.

- **“key concept” does not necessarily mean a diagnostic finding.** Because they collect closed-ended answers, the dictionary can also contain modality names, laterality, and generic answers such as “yes” or “no.” It captures the dataset’s answer vocabulary, not exclusively expert-selected clinical concepts.





## This paper:
The intended benefit is straightforward: **spend less training effort reproducing routine wording and more on domain-relevant answers.** Whether that preserves reasoning or improves visual grounding must be established experimentally.

The proposed benefit is **reducing unwanted learning from repetitive answer formats**.(TODO: does this issue exactly in my training method)

Their hypothesis is: **supervise the important concept while putting less pressure on the surrounding language, preserving more of the pretrained model’s behavior.**


	There is a fundamental ambiguity here: **a model can predict the correct medical term using visual evidence, question wording, or learned answer priors.** This loss rewards the correct term without distinguishing how the model obtained it. It could therefore improve answer accuracy without improving grounding.

