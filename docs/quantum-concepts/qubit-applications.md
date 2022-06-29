# Applications of Qubits outside of Algorithms

Before we talk about designing algorithms using qubits and quantum gates, we can look at a couple of applications of qubits themselves.
For one, there are infinite possible values for the amplitudes of the $\ket{0}$
and $\ket{1}$
states of a qubit, so we can try to pack more data into a qubit. Not that since measurement only yields a 0 or 1, we can't extract more than one bit of data. But this
one bit could still answer some kind of yes-or-no question about the data that was packed into the qubit. Let's consider the following problem

## Aaronson-Drucker Coin Problem

Suppose you are given a coin that is either fair (the probability of getting heads is 0.5) or biased towards heads by a known amount (the probability of
getting heads is $0.5+\theta$
for some known $\theta>0$). Can you determine if you have the fair coin or not? 

The only way you can figure this out is by repeatedly flipping the coin and keeping track of the number of heads and tails. Stastics tells us that we would have to
flip the coin an order of $\frac{1}{\theta^2}$
times to reliably figure out if there is a bias. This would require $\text{log}(1/\theta^2)$
bits of storage to keep track of the numbers of heads and tails. Instead, you could keep track of this count with a single qubit.

We will need two arbitrary rotation gates, $R_x(\theta)$
and $R_x(-\theta)$,
which perform a counterclockwise (resepectively clockwise) rotation by angle $\theta$
in the palm-plex plain. The procedure is as follows:

1. Initilize the qubit to $\ket{0}$
2. Flip the coin. If it comes up heads, apply $R_x(\theta)$,
   and if it come up tails, apply $R_x(-\theta)$.
3. Repeat step two $\lfloor \pi/(4\theta^2)\rfloor$
  times. (we'll get to the reason for this later)
4. Measure the qubit

If the coin was fair, then we expect their to be roughly the same number of clockwise and counterclockwise rotation, so that the final state of the qubit
is pretty close to $\ket{0}$.
Thus, we expect to measure a 0. If on the other hand, the coin was biased, then at any given flip the probability of counterclockwise rotation is $0.5+\theta$
and the probability of clockwishe rotation is $0.5-\theta$.
Thus, we expect a counterclockwise rotation by angle
$$\left(\frac{1}{2}+\theta\right)(\theta)+\left(\frac{1}{2}-\theta\right)(-\theta)=2\theta^2.$$
Thus performing roughly $\frac{\pi}{4\theta^2}$
coins flips achieves an expected rotation of $\frac{\pi}{4\theta^2}\cdot2\theta^2=\frac{\pi}{2}$.
Thus, for a biased the probability of measuring the qubit as being in the $\ket{1}$
state is quite high. 

We see here how we can load a bunch of data (the outcomes of all the flips) into a qubit and measuring it can tell us something about that data.
