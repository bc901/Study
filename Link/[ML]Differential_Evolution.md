<a href="https://en.wikipedia.org/wiki/Differential_evolution"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Ackley.gif/220px-Ackley.gif" title="GA" alt="GA_Flow"></a>



# Differential Evolution

Differential evolution (DE) method, introduced by Price and Storn, is one of the most recent global optimizers, which also has been applied to estimate the values of the system parameters in some contexts. The first paper about genetic annealing was published in the October 1994 issue of Dr. Dobb's Journal by K. Price. It was a population-based combinatorial algorithm that realized an annealing criterion via thresholds driven by the average performance of the population. Soon after this development, Price was contacted by R. Storn, who was interested in solving the Chebyshev polynomial fitting problem by genetic annealing. After some experiments Price modified the algorithm using floating-point instead of bit-string encoding and arithmetic vector operations instead of logical ones. These recasts have changed genetic annealing from a combinatorial optimizer into a continuous one. In this way, he discovered the procedure of differential mutation. Price and Storn detected that differential mutation combined with discrete recombination and pairwise selection does not need an annealing factor. Therefore, the annealing mechanism had been finally removed and thus the obtained algorithm stated the era of Differential evolution (ref.Storn1997). It was described by Price and Stron in the ICSI technical report "Differential evolution-A simple and efficient adaptive scheme for global optimization over continuous spaces", 1995.

In the evolutionary computation, differential evolution optimizes a problem by iteratively trying to improve a candidate solution with regard to a given measure of quality. Global optimisation is necessary in fields such as engineering, statistics and finance. But many practical problems have objective functions that are non differentiable, non-continuous, non-linear, noisy, flat, multi-dimensional or have many local minima, constraints or stochasticity. DE does not use the gradient of the problem being optimized, which means it does not require special conditions for the proprieties of the objective function and constraints. It can therefore also be used on optimization problems that are not even continuous, are noisy, change over time and it is extensible on multi-modal and multi-objective optimization. It provides excellent precision, fast convergence and self-adaptation. However, there are some disadvantages such as lack of strong convergence proof and sensitivity of the control parameters.

Differential evolution consists of 3 main steps of mutation, crossover and selection operators. In this population-based direct-search algorithm, a set of solutions simultaneously progresses towards the optimum. A basic variant of the DE algorithm works by having a population of candidate solutions, called agents. These agents are moved around in the search-space by perturbations like other population-based methods, but these deviations are neither reflections like Nelder-Mead methods, nor samples from a predefined probability density function. Instead, DE produces the mutant agents using the scaled difference of two randomly selected population vectors in mutation step. The crossover step allows the construction of a new trial element starting from the current and mutant elements. Thus it controls which and how many components are mutated in each element of the current population. In the selection, if the new position of an agent is an improvement it is accepted and forms part of the population, otherwise the new position is simply discarded. The process is repeated until a satisfactory solution will eventually be discovered. 

####[Step 1: Initialization]
The initial population of possible solution vectors x<sub>i</sub> : i = 1, 2, ..,N<sub>p</sub> are generated by random sampling in the search-space. Each element of a solution vector of dimension D<sub>v</sub> is denoted by 

<ol>x<sub>i</sub> = [x<sub>{i,j}</sub> : j=1, 2, ...,D<sub>v</sub>].</ol>

####[Step2 : Mutation] 
Mutant vectors v<sub>i</sub> are generated according to 

<ol>v<sub>i</sub>=x<sub>best</sub>+P(x<sub>m</sub>-x<sub>n</sub>) i=1, 2, ...,N<sub>p</sub></ol>

where x<sub>best</sub> is the best solution, {x<sub>m</sub>,x<sub>n</sub>} are two distinct arbitrary candidate solution vectors and P = (0, 2) is a mutation scale factor. 

####[Step3 : Crossover]
A set of vectors u<sub>i</sub> are formed for each i=1, 2, ...,N<sub>p</sub>,

<ol>u<sub>{i,j}</sub> is determined to 2 cases:</ol>

<ol>v<sub>{i,j}</sub>, if rand<sub>j</sub>(0,1) < C<sub>R</sub></ol>

<ol>x<sub>{i,j}</sub>, otherwise.</ol>

where j=1,2,...,D<sub>v</sub> and C<sub>R</sub> = [0,1] is a crossover probability.

####[Step4 : Selection]
The next generation vectors x<sub>i</sub> are selected as 2 cases:

<ol>u<sub>i</sub>, if J(u<sub>i</sub>) < J(x<sub>i</sub>)</ol>

<ol>x<sub>{i,j}</sub>, otherwise.</ol>

Repeat steps 2-4 until the termination criteria are met. 



In the algorithm, the scale factor "P" gives the scatter around of x<sub>best</sub> in mutation step. The stated range for P is (0,2) and it has required P>1 to be successfully optimized result, in general. This is not to say that solutions are not possible when P>1, but only that they tend to be both more time consuming and less reliable than if P<1. We will demonstrate this fact numerically using an example. C<sub>R</sub>, called a crossover probability, determines how much preference is given to mutant in recombination of components in each solution vector. The average number of parameters mutated depends on the crossover model and a low C<sub>R</sub> corresponds to a low mutation rate. Many genetic algorithms recommend a crossover probability of 1/D<sub>v</sub> that D<sub>v</sub> is the dimension of a solution vector, meaning that, only one trial parameter is mutated on average. 

DE optimizes a problem by maintaining a population of candidate solutions and creating new candidate solutions, and then keeping whichever candidate solution has the best fitness on the optimization problem. In details, mutation expands the search space, crossover incorporates candidate solutions from the previous generation and new candidate solutions for recombination, and selection admits the one with the lowest function value to the next generation. Therefore, selection tends to reduce the diversity of a population, whereas mutation and crossover increase it. To avoid premature convergence, it is crucial that F and C<sub>R</sub> be of sufficient magnitude to counteract the selection pressure. The choice of parameters N<sub>p</sub>, P, and C<sub>R</sub> in differential evolution algorithm can have a large impact on optimization performance, in general. Selecting parameters yielding good performance has therefore been the subject of much research. 


**Reference**

- https://www.aimspress.com/fileOther/PDF/MBE/1551-0018_2018_3_667.pdf (My published paper ^^;)
- https://www.youtube.com/watch?v=BCp_kfuPWvs
- Karabogka, 2004, A simple and global optimization algorithm for engineering problems: Differential evolution, 53p-60p.
- Storn, 1996, Differential evolution design of an IIR-filter with requirements of magnitude and group delay, 268p-273p.
- Storn, 1997, Differential evolution-a simple and efficient heuristic strategy for global optimization over continuous spaces, 341p-359p.
- Storn, 1999, System design by constraint adaptation and differential evolution, 22p-34p.