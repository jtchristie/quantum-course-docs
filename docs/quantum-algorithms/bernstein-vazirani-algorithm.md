# Bernstein-Vazirani Algorithm

## Another toy problem

Much like the Deutsch-Jozsa problem, the Bernstein-Vazirani problem is toy problem where you are given a black box function that you want to learn about with
as few iterations as possible. Just like before, the black box function takes in $n$
bits of input and outputs a single bit:

```c#
public bool BlackBox(bit[] Input)
```

However, in this case instead of having a constant or balance function, we know that the oracle function, $f$,
performs a bitwise dot product of the input bit string $x=x_0x_1...x_{n-1}$
with some fixed (albeit unknown) bit string $s=s_0s_1...s_{n-1}$.
That is
$$f(x)=(s_0x_0)\oplus (s_1x_1)\oplus...(s_{n-1}x_{n-1}).$$

The goal here is to find out the value of the mystery string, $s$,
with as few iterations of the function as possible. Classically, we know that we can figure out $s$
with $n$
iterations of the function. We can probe the function by inputing a string with the $i$
-th bit set to 1 and all other bits set to 0. Then the function will output the value of $s_i$.
Since we get one bit of information per iteration of the function, we can't figure out $s$
in less than $n$
iterations. Using a quantum algorithm, however, we can figure out the $s$ in one iteration!

## Implementing the Oracle

If we were told to classically implement such a function, $f$,
and were given the string $s$,
how would we do it? First, we could notice that if an bit of $s$,
$s_i$,
was zero than the value of $x_i$
has no impact on the output of $f$.
Thus, we can leave these bits in the register alone. On the other hand, if $s_i=1$,
then toggling $x_i$
between 0 and 1 flips the value of the resulting $f(x)$.
We can implement this by adding a CNOT gate for every non-zero bit, $s_i$,
which will have the $i$
-th bit as a control and the output bit as a target.

As an example if $s=011$, then an implementation of $f$ would like

![bv-1](images/bv-1.png){: .center loading=lazy}

