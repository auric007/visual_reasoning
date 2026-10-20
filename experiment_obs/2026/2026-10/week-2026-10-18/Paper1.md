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
4. 