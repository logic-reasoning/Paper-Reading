# Paper-Reading


## Graph Models
 
### KagNet: Knowledge-Aware Graph Networks for Commonsense Reasoning
- Key idea: utilizes external, structured knowledge graphs to perform explainable inferences.
- Framework: Given the question-answer pairs, they use two kinds of inputs to the GCN-LSTM-HPA network.
   - (1) The embedding of Q/A.
   - (2) Search the paths between Q and A, and then generate paths to build graphs.  

### Can Graph Neural Networks Help Logic Reasoning?

## Neural Networks

### Neural Logic Machines

### Differentiable Learning of Logical Rules for Knowledge Base Reasoning 

- Key idea: Use the given relations in the knowledge base to generate new relations. Use a matrix to represent the relations between entities to make it trainable.
- Inspiration: How to represent the discrate rules to the continues space. 
- Limitation: The logics are very simple, only could be like A->B, B->C, then A->C.

### Neural Probabilistic Logic Programming in DeepProbLog



