# A visual proof that neural nets can compute any function

One of the most striking facts about neural networks is that they can compute any function at all. That is, suppose someone hands you some complicated, wiggly function, f(x):

<p align="center">
  <img src="https://user-images.githubusercontent.com/77112891/164579614-b313ca72-6eb7-4ce3-9fc3-acc493dabeed.png" width="200"/>
</p>

No matter what the function, there is guaranteed to be a neural network so that for every possible input, x, the value f(x) (or some close approximation) is output from the network, e.g.:

<p align="center">
  <img src="https://user-images.githubusercontent.com/77112891/164580031-26343673-e40b-456c-b52a-881743213711.png" width="200"/>
</p>

This result holds even if the function has many inputs, f=f(x1,…,xm), and many outputs. For instance

<p align="center">
  <img src="https://user-images.githubusercontent.com/77112891/164580100-6d5984c9-054d-43d5-8984-53c30ee59220.png" width="200"/>
</p>

This result tells us that neural networks have a kind of universality. No matter what function we want to compute, we know that there is a neural network which can do the job.

What's more, this universality theorem holds even if we restrict our networks to have just a single layer intermediate between the input and the output neurons - a so-called single hidden layer. So even very simple network architectures can be extremely powerful.

The universality theorem is well known by people who use neural networks. But why it's true is not so widely understood. Most of the explanations available are quite technical. For instance, one of the original papers proving the result<sup>[*](#fn1)</sup> did so using the Hahn-Banach theorem, the Riesz Representation theorem, and some Fourier analysis. If you're a mathematician the argument is not difficult to follow, but it's not so easy for most people. That's a pity, since the underlying reasons for universality are simple and beautiful.

<a name="fn1">*</a>[Approximation by superpositions of a sigmoidal function](https://sites.dartmouth.edu/cybenko/), by George Cybenko (1989). The result was very much in the air at the time, and several groups proved closely related results. Cybenko's paper contains a useful discussion of much of that work. Another important early paper is [Multilayer feedforward networks are universal approximators](https://www.sciencedirect.com/science/article/abs/pii/0893608089900208), by Kurt Hornik, Maxwell Stinchcombe, and Halbert White (1989). This paper uses the Stone-Weierstrass theorem to arrive at similar results. 

In this chapter I give a simple and mostly visual explanation of the universality theorem. We'll go step by step through the underlying ideas. You'll understand why it's true that neural networks can compute any function. You'll understand some of the limitations of the result. And you'll understand how the result relates to deep neural networks.

To follow the material in the chapter, you do not need to have read earlier chapters in this book. Instead, the chapter is structured to be enjoyable as a self-contained essay. Provided you have just a little basic familiarity with neural networks, you should be able to follow the explanation. I will, however, provide occasional links to earlier material, to help fill in any gaps in your knowledge.

Universality theorems are a commonplace in computer science, so much so that we sometimes forget how astonishing they are. But it's worth reminding ourselves: the ability to compute an arbitrary function is truly remarkable. Almost any process you can imagine can be thought of as function computation. Consider the problem of naming a piece of music based on a short sample of the piece. That can be thought of as computing a function. Or consider the problem of translating a Chinese text into English. Again, that can be thought of as computing a function<sup>[*](#fn2)</sup>. Or consider the problem of taking an mp4 movie file and generating a description of the plot of the movie, and a discussion of the quality of the acting. Again, that can be thought of as a kind of function computation<sup>[*](#fn3)</sup>

<a name="fn2">*</a>Actually, computing one of many functions, since there are often many acceptable translations of a given piece of text.

<a name="fn3">*</a>Ditto the remark about translation and there being many possible functions.. Universality means that, in principle, neural networks can do all these things and many more.

Of course, just because we know a neural network exists that can (say) translate Chinese text into English, that doesn't mean we have good techniques for constructing or even recognizing such a network. This limitation applies also to traditional universality theorems for models such as Boolean circuits. But, as we've seen earlier in the book, neural networks have powerful algorithms for learning functions. That combination of learning algorithms + universality is an attractive mix. Up to now, the book has focused on the learning algorithms. In this chapter, we focus on universality, and what it means.
