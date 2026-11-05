https://www.mdpi.com/2079-9292/15/19/4461

It investigates how to construct a smaller, more useful instruction-tuning dataset. The key contribution is therefore the data-construction process rather than a new selection algorithm.

Instruction tuning data can have several problems
- Redundancy: Thousands of samples teach essentially the same capability.
- Incorrect supervision: Some answers are wrong, ambiguous, or poorly grounded in their images.
- Capability imbalance: The dataset may contain many simple recognition questions but very few compositional reasoning questions.

This paper will help us with:
Can we select useful samples, repair imperfect ones, generate missing types of supervision, and then select again while keeping the final dataset size fixed?

