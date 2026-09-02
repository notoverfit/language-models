## Long short-term memory for next word prediction

The research in this directory is inspired by ["Generating Sequences with Recurrent Neural Networks" by Alex Graves (2014)](./graves_2014.pdf). 

Recurrent neural networks (RNN) work in two dimensions - a hidden-layer dimension (which goes through the hidden layers of the network), as well as through time/iterations/steps. 

The key idea of a RNN is that at each hidden layer $h^{(1)}, h^{(2)}, \dots$, there is also a "time" dimension $h^{(1)}_t, h^{(2)}_t, \dots$. Thus, at the first layer and at time $t$, the output of that layer is a function given by

$$ h^{(1)}_t = f(x_t, h^{(1)}_{t-1})$$

where $x_t$ is the input of the network. This has a few interesting characteristics specifically for word generation.
- Previous words in a sequence (where "time" is now instead the $i$-th word of a sequence) can provide context for future words
- Backpropagation can flow through two dimensions (through the network and through the sequence)

