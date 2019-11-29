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
 
### Neural Logic Machines
 - build the computational graph according to input logical expressions, dynamically construct the architecture
    ![avatar](figures/ipeline.jpg)
     - variables in the logic expressions are represented as vectors of the same dimension
     - each basic logic operation (AND/OR/NOT) is learned as a neural module (MLP) during the training process
     - add logic regularizers over the neural modules to guarantee that each module conducts the expected logical operation
     - Sim is a neural module to calculate the similarity between two vectors
    ![avatar](figures/similarity.jpg)
     - loss
        ![avatar](figures/loss.jpg)
         - Lc: classification loss, cross entropy loss
         - Rl: logic regularizer
        ![avatar](figures/regularizer.jpg)
         - RΙ: length regularizer, constrain the vector length
         - RΘ: l2 regularizer, prevent overfitting

### Learning to Annotate: Modularizing Data Augmentation for Text Classifiers with Natural Language Explanations
 - augment training data for text classification using NL explanations
 - problem setting: we want to learn X->Y, only a subset x with labels y and explanations e (how the decision is made)
 ![avatar](figures/NPL_example.jpg)
   - problem: the existence of linguistic variants (e.g. reasonable price/fair price; fair enough price) - this paper uses soft match to solve this problem
 - method:
   - parse NL explanations into logical forms by a combinatory categorial grammar (CCG) based semantic parser
   - partial corpus are labeled by the extracted logical forms using exact matching
   - the rest of corpus are labeled by neural module networks
   - train a final classifier with both corpus
   ![avatar](figures/NEXT_overview.jpg)
 - more specifically
   - train: for each (xj, ej, yj), we learn ej ->(CCG)-> fj -> yj
   - inference for data augmentation: for each x' in raw corpus
      - if fj exists in (exact match) x', then we assign yj as label to x', get (x', yj) as labeled dataset
      - if no fj exact match x', then get (x') as unlabeled dataset. And use neural module network and soft-match (much detail design in the paper) to assign pseudo labels
   - use labeled dataset and unlabeled dataset to train the classifier
      - neural module network and classifier are jointly trained

### Probabilistic Logic Neural Networks for Reasoning
    - Authors: Meng Qu, Jian Tang
      [[https://arxiv.org/pdf/1906.08495.pdf][Link]]
    - Goal: 
      1. Link prediction in knowledge base.
      2. Exploit first-order logic rules, handling their uncertainty, and infer missing triplets.
    - Method: triplets distribution defined with Markov Logic Network. 
      1. In E-step, infer plausibility of unobserved triplets.
      2. In M-step, update weights of logic rules. 
    - What are the rules?
      Mined from the knowledge base. Including composition rules, 
      inverse rules, symmetric rules, and subrelation rules. 
      So, each rule is concerned with relations: sth like if (x r y) then (y r x).



### Can Neural Networks Understand Logical Entailment? [ICLR 2018]
    Authors from Deepmind.
    [[https://openreview.net/pdf?id=SkZxCk-0Z][Link]]
    - Quick summary:
      The paper aim to solve entailment. The entailment in this paper is purely based on 
      the structure of formal logic. For example, \(p\land q \rightarrow q\) is a true 
      entailment, irrelevant of what \(p\) and \(q\) stand for and what specific 
      proposition that the entailment stands for. 

      A dataset is created for the training and verification of such task. 

      Interestingly, their proposed method assumingly outperforms TreeRNN (recusrive RNN).
 

 ### TensorLog: A Differentiable Deductive Database [2016]
    - Author: William W. Cohen
    [[https://arxiv.org/pdf/1605.06523.pdf][Link]]
    - Goal: a differentiable reasoning system based on knowledge base.
    - Each clause in a logical theory is converted into certain type of factor graph.