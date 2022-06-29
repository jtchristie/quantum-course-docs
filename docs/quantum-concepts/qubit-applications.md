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

## Elitzur-Vaidman bomb

If you thought the premise of the coin problem was a little far-fetched, just wait till you hear about the Elitzur-Vaidman bomb tester. Suppose you
work for the Quantum Bomb Squad and recieve a suspicious package at the office. The package has peepholes at opposite ends through which a qubit can be sent (perhaps a photonic qubit). It also has a  note saying that the box is either empty of contains a bomb. The note also says the potential bomb would have a measurement device set up behind the peephole, which will detonate the bomb if it measures a 1 from a qubit coming in through the peephole (if it
measures a 0 it will just let the qubit pass all the way through out the other peephole). You're goal is to detect if there is a bomb or not while minimizing the chances of settign it off.

You have with you a qubit initialized to $\ket{0}$
and a rotation gate, $R_x(\theta)$.
Applying the gate to $\ket{0}$
yields
$$R_x(\theta)\ket{0}=\cos(\theta)\ket{0}+\sin(\theta)\ket{1}.$$
If $\theta$ is a small angle than the probability of setting off the bomb with this qubit is the probability of measuring $\ket{1}$:
$$|\sin(\theta)|^2\approx \theta^2.$$
Now, hoping you weren't exteremely unluck and detonated the bomb, keep applying $R_x(\theta)$ to the qubit and passing it through the device. If the bomb
was really there, then it would be measuring the qubit each time and (very likely) collapsing it back to $\ket{0}$
state. Thus, after roughly $\frac{\pi}{2\theta}$
trials the qubit would still be $\ket{0}$
assuming the bomb never measured a $\ket{1}$. 
Using more physics estimation tricks, we can roughly calculate the proability that the bomb doesn't detonate:
$$(1-\theta^2)^{\pi/(2\theta)}\approx 1-\frac{\pi}{2\theta}\theta^2=1-\frac{\pi}{2}\theta,$$
which can be made as close to 1 as you want as long as you are willing to decrease $\theta$
perform more trials.

On the other hand, if there was a never bomb then the qubit what pass through unaffected each time and you would have applied roughly $\pi/(2\theta)$
rotations by angle $\theta$
which would put the qubit in $\ket{1}$
state. To summarize the procedure:

1. Initialize the qubit to $\ket{0}$.
2. Apply  $R_x(\theta)$
   to the qubit and pass it through the box.
3. Repeat the previous step $\lfloor \pi/(2\theta)\rfloor$
   times
4. Measure the qubit. If you get 0, then there is a bomb. If you get a 1, then there is no bomb.

The process that occured is related to something called the **Quantum Zeno** or **Watched Pot Effect**. Essentially, when there is no person or device to measure a qubit it can slowly drift to change its state to something new. On the other hand, if something is constantly measuring the qubit, it has a smaller probability
of changing state from the one it was initialized to.

## Quantum Key Distribution (the BB84 scheme)

In addition to [superdense coding](https://stem.mitre.org/quantum/quantum-algorithms/superdense-coding.html), there is another quantum methadology for secure
communication between two parties, Alice and Bob, that avoids nasty eavesdropper Eve.
