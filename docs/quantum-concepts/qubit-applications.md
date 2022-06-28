# Applications of Qubits outside of Algorithms

Before we talk about designing algorithms using qubits and quantum gates, we can look at a couple of applications of qubits themselves.
For one, there are infinite possible values for the amplitudes of the $\ket{0}$
and $\ket{1}$
states of a qubit, so we can try to pack more data into a qubit. Not that since measurement only yields a 0 or 1, we can't extract more than one bit of data. But this
one bit could still answer some kind of yes-or-no question about the data that was packed into the qubit. Let's consider the following problem

## The Coin Problem

Suppose you are given a coin that is either fair (the probability of getting heads is 0.5) or biased towards heads by a known amount (the probability of
getting heads is $0.5+\theta$
for some known $\theta>0$). Can you determine if you have the fair coin or not? 

The only way you can figure this out is by repeatedly flipping the coin and keeping track of the number of heads and tails. Stastics tells us that we would have to
flip the coin an order of $\frac{1}{\theta^2}$
times to reliably figure out if there is a bias. This would require $\text{log}(1/\theta^2)$
bits of storage to keep track of the numbers of heads and tails. Instead, you could keep track of this count with a single qubit.

We will need two arbitrary rotation gates, $R_x(\theta)$
and $R_x(-\theta)$.


