# Transport-in-normal-superconducting-normal-junction

About the project:

This Mathematica code was run on the Harvard cluster to obtain the conductance of a normal-superconducting-normal junction, see M. Kanasz-Nagy et al., "Anomalous Conductances in an Ultracold Quantum Wire", Physical Review Letters 117, 255302 (2016), https://arxiv.org/pdf/1607.02509.pdf.

The physical system we considered here was an ultracold atomic realization of a nano-wire (D. Hussmann et al., "Connecting strongly correlated superfluids by a quantum point contact", Science 350, 1498 (2015), https://arxiv.org/pdf/1508.00578.pdf). We were interested in how much current and spin current flows through it when there is a bias voltage applied to the two sides of the sample. 

This looks like a very simple question. However, the ultracold atomic realization was realized in a parameter regime where the usual nanowire experiments haven't gone so far, and it found a very strange behavior. Based on decades of experimental and theoretical work on quantum wires, the expectation was that the conductance of the wire would be at most twice the conductance quantum. However, the experiment found much larger values than this. Furthermore, this value could be tuned by changing the interaction between the atoms.

The interaction between the atoms was very large, and combined with the effect of the confining potential, made the wire superconducting, whereas the surrounding gas was in the normal phase, creating a so-called normal-superconducting-normal junction.



About the code:

First of all, the code in the form it can be viewed here on GitHub is very hard to read. It should be opened in Mathematica so that it becomes readable. Note also that I used Mathematica as a functional programming language in this project. I set up a many functions ('Modules') that were combined in each part of the calculation. The whole code ran within the same notebook.

At the beginning of the simulation, one can set up the parameters of the system, see the comments in the code and the paper. The potentials are spatially dependent, therefore we determine the superconducting order parameter Delta at each point along the wire. Once we have the superconducting profile, we use an S-matrix calculation to determine the conductance and the spin conductance.

The code is structured as follows:
- 'System parameters': here one can set all the physical parameters
- 'Common definitions for both calculations': set up the transverse harmonic modes and their matrix elements in laboratory frame and in the center of mass frame
- 'Definitions for the BCS calculation': These are the functions that are used to determine the free energy of the system. This has a rather complicated integral form (see the paper), please read the paper to follow through the definitions. To calculate the free energy, I had to write a Romberg integration routine qromb (see Numerical Recipies), which also uses a polynomial interpolation for vector, matrix and tensor values, called polint. qromb is much-much faster than the NIntegrate routine of Mathematica. The numerical minimization of the free energy is done in the routine Find\[CapitalDelta]00.


