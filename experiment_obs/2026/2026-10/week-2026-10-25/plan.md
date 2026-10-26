## This week's TODO

- [ ] **1. Compare VLM vs Stage2 YOLO errors — first priority.** Align permanent GT IDs and compatible scenes/taxonomy/IoU; list shared misses, unique successes, misclassifications and false positives. Saved-output discovery is starting; no new model inference is required if the outputs are complete.
- [ ] **2. Define and run a new VLM training experiment.** First settle the data/recipe change and baseline; inspect final inputs for label leakage. Training is not launched by this checklist; CUDA currently reports no available device.
- [ ] **3. Read the grounding/data-selection papers and define the paper-based experiment.** Previous reading list: arXiv2307.13702 and2510.01454. Choose a testable hypothesis before implementing or running it; these papers have not been newly read in this session.

## Time to set aside

- [ ] Reserve focused time this week to review the VLM–YOLO comparison and inspect the disagreement instances.
- [ ] Reserve time to prepare/review the next training data and agree the experiment question.
- [ ] Reserve time for the two papers, notes, and translating one idea into an experiment.