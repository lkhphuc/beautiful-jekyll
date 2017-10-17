---
layout: post
title: Short introduction about Quantum Computer and Quantum Cryptography
subtitle: What is it and why it's interesting with no complex physics
bigimg: /img/quantum/entanglement.jpg
---
In recent years, beside the *Conventional Computer*, a new type of computer called *Quantum Computer* has received a lot of attention and is in very active development. The Quantum computer is based on *Quantum Mechanics*, compare to the conventional computer that is based on mathematical logic and boolean algebras. There are a lot of application for this new type of computer but one of the most important is *Quantum Cryptography.*

## Layout
- To understand Quantum Cryptography and why it’s so important, I will first give you an overview about Quantum Computer, what it is, how it is built and what is its application. 
- After that, I will dive deep into its most important application, Quantum cryptography. In Cryptography, Quantum computer can both be a threat to current cryptography system and it’s might also enable the creation of first hack-proof encryption scheme.

# Quantum Computer
## Quantum Computer in context
The processing power of conventional computers has exponentially grows over the past few decades as the size of a transistor get smaller and more transistor can be fit on a single chip. Along with that decrease in transistor’s size, the set of intractable problems (the problems that requires more computing power and time than any modern machine could reasonably supply) also gets smaller. When the size of the transistor get close to nanometer level, around 1 or 2 atoms thick, the effect of quantum mechanics kicks in and transistors can no longer be shrunk, but there are still intractable problems cannot be solved yet. 

Because quantum mechanics blocks the advances of conventional computer, scientists used the same Quantum Mechanic to create a new type of computer that can solve problem that was previously intractable with conventional computer.

### What is "Quantum" anyway?
So what is Quantum? It basically means a very tiny amount. So Quantum mechanics  is the studying of the laws that govern the behavior and interaction of matter (Photon, neutron, lepton, quark,.. ) at very small scale (nanometer), at this level the traditional law of physics just does not apply anymore. The basic quantum phenomena that motivates the development of Quantum Computer is *“superposition”*.

## Qubit 
In traditional computer, the most basic level information is bit. A state of a bit is deterministic, that means it can be 0 or 1. Quantum superposition describes a state of a quantum object- quanta, in this case a qubit, and contrary to traditional bit, a qubit can be in any proportion of both states at once. This is called superposition. As long as it is not observed or measured, the qubit is in a superposition of probability of 0 and 1, and you can’t predict what it will return (0 or 1) until you measure it. Utilizing this particular property, a computer of 4 qubits can represents all 16 possible configurations at once, compare to the traditional bit of represent only 1 of the 16 configuration at a time. This number increases exponentially with each qubit added. With a computer of 300 qubits, you have the equivalents of 2 to the 300 bits, which is as many particle in the universe as there are.
Even though it’s can represent all the configuration of traditional bits in parallel with its superposition state, when we measure it, it must return to one of its many state. So it’s not a replacement for traditional computer but only superior for application that takes advantage of the fact that you have all the quantum superposition available to you at the same time, a kind of computational parallelism. So if you want to watch cat videos online super fast in super HD resolution, Quantum computer won’t help much. But if you want to simulate weather, simulate chemical reactions, doing optimization, break current cryptography or create an unbreakable cryptography that is guarantee by physic laws, quantum computer will be in tremendous help.


# Quantum Cryptography

## Quantum Cryptography in context
There are two types of cryptography,, symmetric cryptography that use the same key for encryption and decryption, and asymmetric cryptography that use public and private key for encryption and decryption. Currently, symmetric encryption is fast but limited by the method of sharing the secret key, the most secure way is hand-to-hand but this required participants to meet each others in the first place and thus the secret key cannot be changed often enough. One way to get around this is to use the public key cryptography and signature scheme to initially share the secret key. And that is pretty much how cryptography is applied on the internet today. One of the most popular algorithm of asymmetric cryptography is RSA. Every time you browse the web or send an message, you probably use RSA. The security of RSA is guaranteed by the complexity of factoring problem, which is: given a number, find its prime factors. In traditional computer, the time its take to factor a number increases exponentially with the length of the number, so a large enough number may takes hundred or thousand of years to factor, which is way too long for any practical reason for trying to break the encryption. 
[factor](/img/quantum/factor2.png)
However, with Quantum Computer and its amazingly parallel computing power, large number can be factored efficiently with Shor algorithm, an algorithm created by Peter Shor, an MIT math professor. The time its take to factor big number is no longer exponentially correlated to the input and the reliability of RSA is going away.

When quantum computer that can run the Shor algorithm is created in the near future, there are two directions to pursuit and save the internet’s privacy, that is either we found a different public key encryption scheme that relies on different mathematical problems so complex even Quantum computer can not solve efficiently or we exploit Quantum Mechanical property to create an even better way to encrypt data than public key encryption. 

# Quantum Key Distribution - hack-proof cryptography

One method that exploits Quantum mechanic to create a safer encryption scheme is called *Quantum Key distribution*. Quantum Mechanic is not directly involve the encryption step, the efficient symmetric encryption will still be used. But rather, some quantum properties will be applied to create a secure way to share the secret key between participants. 
Those laws are: the Heisenberg’s Uncertainty principle states that the position and the velocity of an object cannot both be measured exactly, at the same time, even in theory. This implies the Observer effect, the fact that simply observing a quanta necessarily changes it, this is not due to the limits of current technology but it’s guarantee as a fact of nature. And because we cannot know for sure all the characteristics of a quanta at a moment, the no-cloning theorem in physics states that it is impossible to create an identical copy of an arbitrary unknown quantum state. Together, all 3 laws of Quantum Mechanics implies that it is impossible to copy data encoded in a quantum state and the very act of reading data encoded in a quantum state changes the its value. 
This is used to detect eavesdropping in quantum key distribution, if a quantum key has been intervened by a third party, the key is simply dropped before any sensitive data is encrypted using that key. On the other hand, if no tapping was detected, the security of the key is guaranteed by the law of physics.

The field of Quantum Cryptography is in very active development, just last month, the first quantum-encrypted video call was made between China and Vienna. This first demonstration of Quantum key distribution  was made possible with the Chinese’s dedicated quantum satellite: Micius. Two entangled photons in superposition state that encode the secret key was created in the satellite and then transmitted to Beijing and Vienna. This key is then used to encrypt data over traditional VPN network.
[satellite](/img/quantum/satellite.jpg)

## Summary
In summary, Quantum computer exploits the effect of quantum mechanics to solve problems that can utilize the parallel nature of quantum superposition. One of the most important application quantum computer is in Cryptography, where quantum computer is a threat to current RSA asymmetric cryptography but it’s also enable secure way to communicate and the reliability is guaranteed by law of physics.
