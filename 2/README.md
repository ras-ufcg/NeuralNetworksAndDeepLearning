# How the backpropagation algorithm works
In the last chapter we saw how neural networks can learn their weights and biases using the gradient descent algorithm. There was, however, a gap in our 
explanation: we didn't discuss how to compute the gradient of the cost function. That's quite a gap! In this chapter I'll explain a fast algorithm for computing 
such gradients, an algorithm known as backpropagation.

The backpropagation algorithm was originally introduced in the 1970s, but its importance wasn't fully appreciated until a [famous 1986 paper](https://www.nature.com/articles/323533a0) by [David Rumelhart](https://en.wikipedia.org/wiki/David_Rumelhart), [Geoffrey Hinton](http://www.cs.toronto.edu/~hinton/), and [Ronald Williams](https://en.wikipedia.org/wiki/Ronald_J._Williams). That paper describes several neural networks where 
backpropagation works far faster than earlier approaches to learning, making it possible to use neural nets to solve problems which had previously been insoluble. 
Today, the backpropagation algorithm is the workhorse of learning in neural networks.

This chapter is more mathematically involved than the rest of the book. If you're not crazy about mathematics you may be tempted to skip the chapter, and to treat 
backpropagation as a black box whose details you're willing to ignore. Why take the time to study those details?

The reason, of course, is understanding. At the heart of backpropagation is an expression for the partial derivative ∂C/∂w of the cost function C with respect to 
any weight w (or bias b) in the network. The expression tells us how quickly the cost changes when we change the weights and biases. And while the expression is 
somewhat complex, it also has a beauty to it, with each element having a natural, intuitive interpretation. And so backpropagation isn't just a fast algorithm for 
learning. It actually gives us detailed insights into how changing the weights and biases changes the overall behaviour of the network. That's well worth studying 
in detail.

With that said, if you want to skim the chapter, or jump straight to the next chapter, that's fine. I've written the rest of the book to be accessible even if you 
treat backpropagation as a black box. There are, of course, points later in the book where I refer back to results from this chapter. But at those points you should 
still be able to understand the main conclusions, even if you don't follow all the reasoning.
