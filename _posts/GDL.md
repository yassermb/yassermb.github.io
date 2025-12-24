---
title: 'Blog Post number 1'
date: 2012-08-14
permalink: /posts/2012/08/blog-post-1/
tags:
  - cool posts
  - category1
  - category2
---

This is a sample blog post. Lorem ipsum I can't remember the rest of lorem ipsum and don't have an internet connection right now. Testing testing testing this blog post. Blog posts are cool.

Headings are cool
======

You can have many headings
======

Aren't headings cool?
------



What is Geometric Deep Learning?

Often, during events or conferences, when I explain our work I have to mention Geometric Deep Learning (GDL) as a cornerstone of our research. But this usually leads to questions like, "What is Geometric Deep Learning?" or comments like, "This is the first time I'm hearing this term!" Despite being an important and well-established field, I have noticed that it remains relatively obscure, particularly outside specialized areas like structural biology, computer vision, and physics. Understanding this concept is also crucial for grasping emerging technologies, such as de novo protein design. So I thought I'd shine some light and give a simple definition of GDL. I believe this will lay a good foundation for exploring topics like the application of generative AI in therapeutic solutions.



Let's begin with a simple question:



How can we build a model that learns and analyzes the structure of a protein, a highly complex 3D object in the Cartesian system?



We can use traditional deep learning algorithms but then we run into two major challenges:



1. The lack of a global frame of reference. Traditional deep learning algorithms are sensitive to transformations in input data (e.g., image rotation) and might perceive transformed data as a new, unseen sample. In the context of proteins, features like biological function or binding affinity are irrelevant to global translations and orientations of the protein structure.

2. The complexity of the 3D structures leading to the curse of high dimensionality.



GDL addresses these challenges by using low-dimensional geometric priors and associated symmetry groups, ensuring invariance to transformations like rotations and permutations while maintaining the properties of protein structures intact. 



But GDL isn't just about 3D objects! It extends deep learning techniques to non-Euclidean domains like graphs and manifolds. For instance, proteins can be represented as graphs, where amino acids are nodes connected by edges. They can also be represented as meshes or point clouds. Out of all the different ways to represent/learn geometric data, graph representation learning is my favorite. It is an exciting category of architectures known as Graph Neural Networks (GNNs). These networks learn intricate, high-dimensional representations of graphs using propagation (message passing) between nodes via edges. GNNs deserve their own post!









We can represent a protein structure, or any (bio-)molecule, as a graph. Nodes can be amino acids and edges can be covalent or molecular interactions. Nodes communicate with each other and update their feature vectors through a process known as message passing. This representation allows us to leverage graph learning architectures and learn the properties of the structure.



Here are some awesome visualizations that highlight the importance of equivariance in GDL. It's a core feature where the output of an equivariant layer undergoes the same predictable transformation as its input.











            Source: https://github.com/QUVA-Lab/e2cnn



In the world of protein structures, thanks to the local equivariance property, not only does GDL find structural motifs regardless of their position and orientation, but it also considers the relative orientation and position of these motifs which is necessary for the right information aggregation.







          Source: https://onlinelibrary.wiley.com/doi/abs/10.1002/prot.26235



Also, check out this video from [3]:











Many researchers from different groups contributed to this field. Thanks to their mathematically rigorous work, we now have a solid foundation for GDL, with numerous applications across different domains. Here are a few of these references:







Bronstein et al., 2021: "Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges"



Weiler & Cesa, 2019: "General e (2)-equivariant steerable CNNs"



Weiler et al., 2018: "3D steerable CNNs: Learning rotationally equivariant features in volumetric data"



Fuchs et al., 2020: "Se (3)-transformers: 3D roto-translation equivariant attention networks"



Chami et al., 2022: "Machine learning on graphs: A model and comprehensive taxonomy"



In future posts, I'll go deeper into the details and share educational resources where you can learn more about GDL.