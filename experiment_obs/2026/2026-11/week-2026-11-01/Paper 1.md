https://www.mdpi.com/2079-9292/15/19/4461

It investigates how to construct a smaller, more useful instruction-tuning dataset. The key contribution is therefore the data-construction process rather than a new selection algorithm.

Instruction tuning data can have several problems
- Redundancy: Thousands of samples teach essentially the same capability.
- Incorrect supervision: Some answers are wrong, ambiguous, or poorly grounded in their images.
- Capability imbalance: The dataset may contain many simple recognition questions but very few compositional reasoning questions.

This paper will help us with:
Can we select useful samples, repair imperfect ones, generate missing types of supervision, and then select again while keeping the final dataset size fixed?

There are four questions worth discussing as we read:

1. Multi-Criteria Selection: How do they estimate whether a sample is useful? Why combine random sampling, gradient-based selection (LESS-MM), and diversity-based selection (COINCIDE)?
2. Individual Augmentation: How can Qwen2.5-VL validate and correct an answer? What happens when the teacher model itself is wrong?
3. Group Augmentation: How do they identify missing capabilities and generate new samples without introducing incorrect supervision?
4. Experimental reliability: Are the gains attributable to better data, larger intermediate candidate pools, or additional compute? Does improving benchmark averages necessarily improve fine-grained visual reasoning?


Incomplete yet, will read later