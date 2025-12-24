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

The building blocks of geometric deep learning

Geometric deep learning (GDL) addresses two main challenges in classical deep learning: the absence of a global reference frame and the curse of high dimensionality. It leverages low-dimensional geometric priors and an associated symmetry group (𝔾), such as translations, rotations, and permutations, under which certain properties of an object remain invariant. 







The properties of a protein structure (object 𝑜) defined in Euclidean space (domain Ω), such as the binding affinity between two interactors, remain invariant under roto-translation transformations from SE(3) (group 𝔾). We use GDL to design neural networks 𝑓 that conserve these properties.  



Let's set the stage with a few key definitions:



Domain Ω (e.g. 3D Euclidean space) is an underlying space where we can define an object. We apply function space 𝕆 on domain Ω to define object 𝑜 (e.g. a protein 3D structure).


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( \mathbb{O}(\Omega, \mathbb{C})=\{o:\Omega \rightarrow \mathbb{C}\} \)
</p>


where  

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( \mathbb{C} \in \mathbb{R}^d \)
</p>


is the range of values taken by objects defined on Ω.



Group 𝔾 is a set equipped with a binary operation ⊗, known as composition, and satisfies the following properties:







Closure: 


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( \forall g_1, g_2 \in \mathbb{G} \rightarrow g_1 \otimes g_2 \in \mathbb{G} \)
</p>




Associativity: 



<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( \forall g_1, g_2, g_3 \in \mathbb{G} \rightarrow (g_1 \otimes g_2) \otimes g_3 =  g_1 \otimes (g_2 \otimes g_3) \)
</p>



Identity: 


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( \forall g \in \mathbb{G}, \exists! e \in \mathbb{G} → (g \otimes e) = (e \otimes g) = g \)
</p>




Inverse: 


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( \forall g \in \mathbb{G}, \exists! g^{-1} \in \mathbb{G} → g \otimes g^{-1} = g^{-1} \otimes g = e \)
</p>



Each transformation g ∈𝔾 has a representation 𝑝⁡(g). For example, if g is a translation in Euclidean space then,  


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>\( p(g) \in \mathbb{R}^3 \)
</p>



is a translation matrix.



If domain Ω is symmetrical under group 𝔾 then it ensures that the properties of the object 𝑜 remain unchanged despite transformations defined within 𝔾. The Euclidean space is endowed with roto-translation symmetries and the group that contains the roto-translation transformations is called the special Euclidean group or 𝑆⁢𝐸⁡(𝑛), where n is the number of dimensions. This gives us inductive bias which eventually leads to the definition of invariant and equivariant functions, the building blocks of GDL.



Equivariant block

The function 𝑓1 (e.g. a neural network) is equivariant under the transformation g if applying g to the input object 𝑜 results in the same transformation being applied to the output. GDL employs patch-wise symmetry groups to achieve this and ensures that the entire architecture remains locally equivariant by stacking multiple locally equivariant layers.


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( f_1: \mathbb{O}(\Omega) \rightarrow \mathbb{O}(\Omega) \)
<br><br>
\( f_1(p(g)o) = p(g)f_1(o), g \in \mathbb{G} \)
</p>


where 𝑓1 is a function defined on the object to extract its properties and is equivariant to the group 𝔾.



Invariant block

We can formulate invariant function 𝑓2 (again a neural network) that benefits from the geometric priors of domain Ω:


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( f_2: \mathbb{O}(\Omega) \rightarrow \mathbb{Y} \)
<br><br>
\( f_2(p(g)o) = f_2(o), g \in \mathbb{G} \)
</p>


where 𝑓2 is a function defined on the object to extract its properties and is invariant to the group 𝔾.



In most problems, the final layer is designed to make the whole process globally invariant. The integration of equivariant and invariant blocks minimizes the number of trainable parameters by utilizing kernels with shared weights (a simple example is convolutional neural networks) and removes the necessity for data augmentation. 



Now let's see how we can put together a complete GDL pipeline!



If domain Ω' is a compact (coarse-grained) version of  domain Ω (Ω′ ⊆ Ω), then we can define the building blocks of the GDL approaches:



Linear  𝔾-equivariant layer

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( f_1: \mathbb{O}(\Omega, \mathbb{C}) \rightarrow \mathbb{O}(\Omega', \mathbb{C'}) \)
<br><br>
\( \forall g \in \mathbb{G}, \forall o \in \mathbb{O}(\Omega, \mathbb{C}) \rightarrow f_1(p(g)o) = p(g)f_1(o) \)
</p>



𝔾-invariant layer (global pooling)


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( f_2: \mathbb{O}(\Omega, \mathbb{C}) \rightarrow \mathbb{Y} \)
<br><br>
\( \forall g \in \mathbb{G}, \forall o \in \mathbb{O}(\Omega, \mathbb{C}) \rightarrow f_2(p(g)o) = f_2(o) \)
</p>



Local pooling (coarsening) 


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( p: \mathbb{O}(\Omega, \mathbb{C}) \rightarrow \mathbb{O}(\Omega', \mathbb{C}) \)
</p>


Nonlinearity


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( \sigma: \mathbb{O}(\Omega, \mathbb{C}) \rightarrow \mathbb{O}(\Omega, \mathbb{C'}) \)
</p>


Now we simply concatenate these blocks to create 𝔾-invariant function:


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<p>
\( \mathbb{F}: \mathbb{O}(\Omega, \mathbb{C}) \rightarrow \mathbb{Y} \)
<br><br>
\( \mathbb{F} = f_2 \odot \sigma_n \odot f_{1,n} \odot p_{n-1} \odot ... \odot p_1 \odot \sigma_1 \odot f_{1,1} \)
</p>



Two standout GDL frameworks that incorporate equivariant and invariant blocks are Graph Neural Networks (GNNs) and Group Equivariant Convolutional Networks (G-CNN). These are widely used in computational and structural biology for many tasks, including quality assessment of protein structure models, protein structure prediction, protein interface prediction, and protein design.



I highly recommend the resources below. Back in 2021, I enjoyed reading [1]! It was so well-explained and easy to follow - I learned a lot from it.



[1] Bronstein et al., 2021: "Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges"

[2] https://geometricdeeplearning.com/



Here are also some amazing resources from Amsterdam Machine Learning Lab (AMLab) and the University of Amsterdam,

Hands-on notebooks: GDL - Regular Group Convolutions and Group Equivariant Neural Networks.

Lectures on Group Equivariant Deep Learning 



This blog is also nice:

Geometric Deep Learning: Group Equivariant Convolutional Networks