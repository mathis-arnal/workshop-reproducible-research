---
title: "Taxonomic Assignment"
teaching: 30
exercises: 15
questions:
- "How can I know to which taxa my sequences belong?"
objectives:
- "Understand how taxonomic assignment works."
- "Use Kraken to assign taxonomies to reads and contigs."
- "Visualize taxonomic assignations in graphics."

keypoints:
- "A database with previously gathered knowledge (genomes) is needed for taxonomic assignment."
- "Taxonomic assignment can be done using Kraken."
- "Krona and Pavian are web-based tools to visualize the assigned taxa."
---
## What is a taxonomic assignment?

A taxonomic assignment is a process of assigning an Operational Taxonomic
Unit (OTU, that is, groups of related individuals) to sequences that can be 
reads or contigs. Sequences are compared against a database constructed using complete genomes. When a sequence finds a good enough match in the database, it is assigned to the corresponding OTU. The comparison can be made in different ways.  

### Strategies for taxonomic assignment  

There are many programs for doing taxonomic mapping, 
and almost all of them follow one of the following strategies:  

1. BLAST: Using BLAST or DIAMOND, these mappers search for the most likely hit 
for each sequence within a database of genomes (i.e., mapping). This strategy is slow.    
  
2. Markers: They look for markers of a database made a priori in the sequences 
to be classified and assigned the taxonomy depending on the hits obtained.  

3. K-mers: A genome database is broken into pieces of length k to be able to search for unique pieces by taxonomic group, from a lowest common ancestor (LCA), 
passing through phylum to species. Then, the algorithm 
breaks the query sequence (reads/contigs) into pieces of length k,
looks for where these are placed within the tree and make the 
classification with the most probable position.  

<a href="../fig/03-06-01.png">
  <img src="../fig/03-06-01.png" alt="Diagram of a taxonomic tree with four levels of nodes, some nodes have a number from 1 to 3, and some do not. From the most recent nodes, one has a three, and its parent nodes do not have numbers. This node with a three is selected." />
</a>
<em> Figure 1. Lowest common ancestor assignment example.<em/>
  
### Abundance bias  
  
When you do the taxonomic assignment of metagenomes, a key result is the abundance of each taxon or OTU in your sample. 
 The absolute abundance of a taxon is the number of sequences (reads or contigs, depending on what you did) assigned to it. 
 Moreover, its relative abundance is the proportion of sequences assigned to it. It is essential to be aware of the many biases that can skew the 
abundances along the metagenomics workflow, shown in the figure, and that because of them, we may not be obtaining the actual abundance of 
the organisms in the sample.

<a href="../fig/03-06-02.png">
  <img src="../fig/03-06-02.png" alt="Flow diagram that shows how the initial composition of 33% for each of the three taxa in the sample ends up being 4%, 72%, and 24% after the biases imposed by the extraction, PCR, sequencing and bioinformatics steps." />
</a>
<em>Figure 2. Abundance biases during a metagenomics protocol. <em/>

  
> ## Discussion: Taxonomic level of assignment
>
> What do you think is harder to assign, a species (like _E. coli_) or a phylum (like Proteobacteria)?
{: .discussion}
  
## Using Kraken 2

[Kraken 2](https://ccb.jhu.edu/software/kraken2/) is the newest version of Kraken, 
a taxonomic classification system using exact k-mer matches to achieve 
high accuracy and fast classification speeds. 

Kraken 2 is available on Galaxy.
We will follow this tutorial, that uses the same dataset: 
https://training.galaxyproject.org/training-material/topics/microbiome/tutorials/taxonomic-profiling/tutorial.html

  