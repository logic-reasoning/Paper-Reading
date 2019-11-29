# Paper-Reading

Note: The (*) indicates the papers that Chao recommended.

## Graph Models
 
### KagNet: Knowledge-Aware Graph Networks for Commonsense Reasoning
- Key idea: utilizes external, structured knowledge graphs to perform explainable inferences.
- Framework: Given the question-answer pairs, they use two kinds of inputs to the GCN-LSTM-HPA network.
   - (1) The embedding of Q/A.
   - (2) Search the paths between Q and A, and then generate paths to build graphs.  

### Can Graph Neural Networks Help Logic Reasoning?

## Neural Networks

### Neural Logic Networks (*)
- the computational graph is built dynamically according to the input logical expression.
- logic expressions are represented as vectors, and each basic logic operation is learned as a neural module during the training process. 
### Neural Logic Machines (*)

### Differentiable Learning of Logical Rules for Knowledge Base Reasoning 

- Key idea: Use the given relations in the knowledge base to generate new relations. Use a matrix to represent the relations between entities to make it trainable.
- Inspiration: How to represent the discrate rules to the continues space. 
- Limitation: The logics are very simple, only could be like A->B, B->C, then A->C.

### Neural Probabilistic Logic Programming in DeepProbLog (*)

- Key idea: query the program for the probabilities of given query atom.
- Framework: 
    - (1) generates all ground instances of clauses in the program the query depends on
    - (2) rewrites the ground logic program into a formula in propositional logic
    - (3) compiles the logic formula into a Sentential Decision Diagram
    - (4) evaluates the SDD bottom-up to calculate the success probability of the given query, starting with the probability labels of the leaves as given by the program and performing addition in every or-node and multiplication in every and-node.
 




## Differentiable Learning of Logical Rules for Knowledge Base Reasoning
- Task: Infering relations in the knowledge base (KB completion).
- Problem: The intuition behind is, if R_k are relations, then 
    R_n(Y, Z_n) and ... and R_1(Z_1, X)	 infers R(Y, X). 
    In other words, if a certain path of relations exists between (Y, X), 
    then a certain relation between them is infered. 
- Method: given 
