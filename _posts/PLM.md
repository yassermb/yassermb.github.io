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

What are Protein Language Models?

Just like human languages, nature has its own unique language—the language of life! This language dictates the cellular mechanisms within all living organisms. By understanding it, we can gain insights into biological processes and answer essential questions, such as: What are the 3D structures of proteins? How do proteins interact? and What are the impacts of mutations on proteins and their interactions?



So how can we understand the language of life? luckily the advances in deep learning algorithms (e.g. transformers and masked language modeling) and the advent of large language models (LLM) have paved the way. Thanks to these algorithms, we now have a class of pre-trained models, known as protein language models (pLM), that help us analyze protein sequences.



Let’s briefly introduce LLMs, which share the same underlying architectures to understand better how pLMs work.





Large Language Models





The Transformer architecture [1]

Large Language Models (LLMs) have revolutionized the field of natural language processing (NLP) with their remarkable ability to understand and generate human languages. Long story short, the most recent breakthrough came with the introduction of transformer architecture [1]. This architecture led to the development of well-known models such as the BERT [2] and the T5 [3] models. These pre-trained models use extensive data and computational resources to learn and extract informative representations from language essential for many downstream tasks in NLP.

These architectures, combined with the ever-growing use of GPUs and the scaling up of data, have led to highly efficient models for text generation. This process involves predicting each word (token) based on the probability distribution derived from the context of preceding words.



Protein Language Models







Protein Language Models (pLMs) apply the same principles from NLP to capture the complex dependencies in protein "sentences". A protein sentence is a sequence of amino acids (i.e. polypeptide) that determine protein properties. pLMs leverage transformer architectures, similar to those used in models like BERT, and help us to predict protein structures and functions. In addition, pLMs have opened up exciting possibilities in protein engineering and synthetic biology. By enabling high-throughput prediction of variant effects, they help us design de novo proteins with desired traits.



pLMs [4-8] are trained on large datasets of protein sequences, such as those from the UniRef databases. These datasets include millions of protein sequences from various organisms and evolutionary backgrounds. Besides using amino acid sequences, some recent models [8] also include structural information represented as a sequence of structural tokens [9] (a structural "sentence") to improve their predictive power.



Two breakthroughs in this field that have significantly advanced research in computational biology and drug discovery are the ProtTrans pLMs [5] and the Evolutionary Scale Modeling (ESM) pLMs [6]. These models extract context-aware embeddings for each amino acid necessary to predict various protein properties like function, stability, structure, inverse folding, and variant effects.









pLMs is a recent class of deep learning models designed to analyze protein sequences by leveraging techniques such as mask language modeling. Here is a timeline showing the evolution of this emerging field. pLMs can be applied in multiple protein-related applications, and some articles explore their diverse uses. To simplify the illustration, I highlighted the primary application of each tool. Similarly, these tools are the result of collaborative efforts across various institutions, and we have noted the key host institutions behind them.



The secret behind protein language models

The recipe of pLM requires five ingredients: 





Large datasets of protein sequences (e.g. UniProt)



Self-supervised learning techniques



Mask language modeling



Transformer architecture (or sometimes LSTM!)

and of course





Computational power (CPU, GPU, and TPU)



The input is protein sequences tokenized into individual amino acids, sometimes accompanied by structural tokens, similar to how words are tokenized in NLP. A portion of the amino acids in the sequences is masked, and using self-supervised techniques the model is trained to predict these masked positions. 



During training, the model learns from the sequence without requiring labeled examples (thanks to self-supervised learning), enabling it to capture the underlying patterns and relationships within protein sequences. The primary objective is to minimize the cross-entropy loss (i.e. log of perplexity), which measures how well the model predicts the masked amino acids based on the rest of the sequence. This metric measures how closely the predicted probability distribution of amino acids matches the desired (target) distribution.




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
    <p>
        \[
        \mathcal{L}(\mathbf{Y}, \mathbf{\hat{Y}}, \mathbf{M}) = - \frac{1}{\sum_{i=1}^n m_i} \sum_{i=1}^n m_i \log P(y_i | \mathbf{S})
        \]
    </p>
    <p>
        \(\mathbf{S} = [s_1, s_2, \ldots, s_n]\)
    </p>
    <p>
        \(\mathbf{Y} = [y_1, y_2, \ldots, y_n]\)
    </p>
    <p>
        \(\mathbf{\hat{Y}} = [\hat{y}_1, \hat{y}_2, \ldots, \hat{y}_n]\)
    </p>
    <p>
        \(\mathbf{M} = [m_1, m_2, \ldots, m_n]\)
    </p>
    <p>
        \(\mathbf{V} = [v_1, v_2, \ldots, v_{20}]\)
    </p>
</body>
</html>




where S represents the input sequence of amino acids, M is a binary array (0 or 1) that indicates the masked positions within S, V is the vocabulary (20 amino acids), Y denotes the ground truth sequence represented by a probability distribution over vocabulary V for each position in the form of one-hot encoding, and Ŷ is the predicted probability distribution over the vocabulary V for each position.  The core of this equation is the following formula



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
<p>
  \(- log P(y_i | \mathbf{S})\)
</p>
</body>
</html>



which is the negative log probability of the correct token yi given the input sequence S. This is the cross-entropy. The formula's simplicity is due to the one-hot encoding of the ground truth Y. Here is why


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
<p>
  \( \hat{y}_i = [P(v_1|S), P(v_1|S),\ldots, P(v_{20}|S)] \)
</p>
</body>
</html>



This is the predicted probability vector for position i over V. 


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
<p>
  \( o_i = [0, 0, 0, 1, \ldots, 0] \)
</p>
</body>
</html>



This is the representation of yi as one-hot encoding over V at position i.  Then


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>
<body>
<p>
  \( Cross Entropy = - \sum_{j=1}^{20}  o_{ij} \times log P(v_j | S) = - log P(y_i | \mathbf{S}) \)
</p>
</body>
</html>




Ok, let's take a break from the math and get back to the fun stuff: applications!



When used for inference, the model functions as an encoder, encoding protein sequences into vector representations (also known as embeddings) that capture their various properties.



pLMs can share their knowledge with other downstream predictive models through a process called transfer learning. This helps boost their performance, particularly for those with a limited amount of labeled data.



Conclusion

pLMs are changing the field of computational biology by providing powerful tools for protein analysis, prediction, and design.



While we are still exploring how deeply pLMs truly grasp or understand the fundamental biophysical properties of proteins, their applications span across multiple domains, making them indispensable in modern biological research. Every year, we see more and more research papers, talks, and posters highlighting how much we rely on pLMs. It’s exciting to see their impact growing!



Stay tuned for our upcoming posts, where we will go deeper into pLMs and uncover the intriguing details behind their impressive performance!



References:

[1] Paper: Attention Is All You Need (Transformer architecture)

[2] Paper: Bidirectional Encoder Representations from Transformers (BERT)

[3] Paper: Text-to-Text Transfer Transformer (T5)

[4] Paper: Protein Sequence Embeddings (ProSE), Code: Github

[5] Paper: ProtTrans, Code: Github

[6] Paper: Evolutionary Scale Modelling (ESM), Code: Github

[7] Paper: ESMFold, Code: Github

[8] Paper: Protein structure-sequence T5 (ProstT5), Code: Github

[9] Paper: FoldSeek, Code: Github



Also here is an excellent blog post on how to use pLMs for protein design and engineering with nice examples:

https://ericmjl.github.io/blog/2024/7/26/a-survey-of-how-to-use-protein-language-models-for-protein-design-part-1/



