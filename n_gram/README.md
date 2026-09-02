## $n$-gram models for next-word prediction

The research in this directory is inspired by ["Class-based n-gram models of natural language" by Brown et.al (1990)](./brown_et_al_1990.pdf).

The natural way to express the problem of next-word prediction is by a sequence of words $\mathbf{x} = (x_1, x_2, \dots, x_n)$ which form a sentence/sentences; for e.g $\mathbf{x} =\verb|the|, \verb|brown|, \verb|fox|, \verb|jumps|, \dots$) as a distribution conditioned on the words that came before the current word. That is
$$P(x_n | x_{n-1}, x_{n-2}, \dots, x_{1})$$
Consider `the brown fox jumps over the lazy dog`. By the word "jumps", we know there is a proper noun and thus a verb is likely to follow it. If we consider the problem of predicting the entire book "Harry Potter and the Philosopher's Stone", your prior should be that the last word in the book likely doesn't have much to do with the first word in the book.

Indeed, we can be fairly greedy with how far we look back. `n`-gram models form distributions for `n`size groups of words (bigram looking at one word prior, trigram looking at three words prior) through the distribution found in the training data. For our example sentence, the bigrams are

$$
\begin{align*}
    &\verb|the => brown| \\
    &\verb|brown => fox| \\
    &\verb|fox => jumps| \\
    &\verb|jumps => over| \\
    &...
\end{align*}
$$

The trigrams should be fairly obvious. After we form the conditional probability distribution for some `n`-gram (we will see for our given data which lookback is optimal), we have two options:
1. Take the most probable word ($\text{arg max}$)
2. Sample from the distribution

Sampling from the distribution causes non-deterministic behaviour which is desirable for many reasons; and is also the approach that modern LLMs take. I won't go into why taking $\text{arg max}$ approaches are generally a bad idea for now, as they will hopefully become evident later on.