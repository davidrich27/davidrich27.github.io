---
title: Research
feature_text: |
   ## My Research
feature_image: "https://picsum.photos/2560/600?image=873"
excerpt: "a heuristic version of the Forward-Backward algorithm, which we have termed the Cloud Search"
aside: true
---

#### Lab: 
###### Wheeler Bioinformatics Lab at the University of Montana


#### Timeline: 
###### Spring 2019 - Spring 2020

### Research Proposal

In the realm of bioinformatics, the task of sequence alignment is a critical component of many research goals, such as gene annotation or homology search. HMMER and MMseqs are two of the most commonly used sequence alignment suites designed for such tasks. These tools both excel in different aspects: MMseqs generally performs the sequence alignment much faster, while HMMER is generally much more accurate.

Broadly speaking, both tools function in much the same way: by taking an entire query and target sequence model, and passing them through a pipeline of increasingly complex and stringent filtering algorithms.  Both of these pipelines utilize the gapped and ungapped Viterbi algorithm.  However, a major differentiator between the two is HMMER’s inclusion of the Forward-Backward algorithm, which computes the sum of the probabilities of all possible alignments of the sequences.  While more computationally expensive, Forward-Backward has been shown to be more effective than Viterbi at recognizing the evolutionary relationships between highly divergent sequences.

As a compromise, we propose a heuristic version of the Forward-Backward algorithm, which we have termed the Cloud Search.  By pruning the search space of Forward-Backward, we hope to drastically reduce the search space, and thus the runtime of the algorithm.  Traditionally, Forward-Backward computes the sum of all probability scores for all possible alignments through a given model – it does this by filling a matrix of size O(N^2) in order to align two sequences of length N.  Though summing over all possible alignments is a key benefit of Forward-Backward, most of the matrix consists of values too small to contribute in any meaningful to the total alignment probability.  Due to state dependencies, this will be accomplished by navigating the dynamic programming matrices in an anti-diagonal fashion, expanding computations out from the centroid of the anti-diagonal until the probability falls below the cut-off.   Through this judicious pruning of only very low probability areas, we believe that these savings should come at minimal cost to accuracy.  This heuristic pruning method bears similarities to algorithms like beam-search and x-drop (used by BLAST).  For a comparative analysis, I will benchmark my algorithm integrated into the HMMER pipeline against current HMMER, MMSEQS, and other state of the art alignment software using a variety of datasets with queries of varying length and identity.
