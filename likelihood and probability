What is the difference between "likelihood" and "probability"?

The answer depends on whether you are dealing with discrete or continous random variables. So, I will split my answer accordingly.

Discrete Random Variables

Suppose that you have a stochastic process that takes discrete values (e.g., outcomes of tossing a coin 10 times, number of customers who arrive at a store in 10 minutes etc). In such cases, we can calculate the probability of observing a particular set of outcomes by making suitable assumptions about the underlying stochastic process (e.g., probability of coin landing heads is p and that coin tosses are independent).

Denote the observed outcomes by O and the set of parameters that describe the stochastic process as θ. Thus, when we speak of probability we want to calculate P(O|θ). In other words, given specific values for θ, P(O|θ) is the probability that we would observe the outcomes represented by O.

However, when we model a real life stochastic process, we often do not know θ. We simply observe O and the goal then is to arrive at an estimate for θ that would be a plausible choice given the observed outcomes O. We know that given a value of θ the probability of observing O is P(O|θ). Thus, a 'natural' estimation process is to choose that value of θ that would maximize the probability that we would actually observe O. In other words, we find the parameter values θ that maximize the following function:

L(θ|O)=P(O|θ)
L(θ|O) is called the likelihood function. Notice that by definition the likelihood function is conditioned on the observed O and that it is a function of the unknown parameters θ.

Continuous Random Variables

In the continuous case the situation is similar with one important difference. We can no longer talk about the probability that we observed O given θ because in the continuous case P(O|θ)=0. Without getting into technicalities, the basic idea is as follows:

Denote the probability density function (pdf) associated with the outcomes O as: f(O|θ). Thus, in the continuous case we estimate θ given observed outcomes O by maximizing the following function:

L(θ|O)=f(O|θ)
In this situation, we cannot technically assert that we are finding the parameter value that maximizes the probability that we observe O as we maximize the PDF associated with the observed outcomes O.

--------------------------------------------------------------------------------

Stochastic Process

A stochastic process is defined as a collection of random variable X={Xt:t∈T} defined on a common probability space, taking values in a common set S (the state space), and indexed by a set T, often neither N or [0, ∞) and thought of as time (discrete or continuous respectively)

A stochastic process is a collection or ensemble of random variables indexed by a variable t, usually representing time.

A stochastic process is any process describing the evolution in time of a random phenomenon.

A stochastic process is a collection or ensemble of random variables indexed by a variable t, usually representing time.

A stochastic process means that one has a system for which there are observations at certain times, and that the outcome, that is, the observed value at each time is a random variable. 

Anything completely random is not important. If there is no pattern in it its of no use.

Even though the toss of a fair coin is random but there is a pattern that given sufficiently large number of trails you will get half of the times as heads. This is a useful pattern.

The pollen in water will follow brownian motion. Even though it appears that motion of individual pollen is independent of its previous direction, overall there is pattern observed with that kind of motion.

In rolling of two dice you may find at any given time the sum of outcome of two dice is random but if you take a series of events ( roll n number of times ) you may observe that 9 and 12 appear less times than 10 and 11. There is a pattern in them even though the individuals are random.

These types of process ( series of events) are called stochastic processes. The individual events are random but there is inherently a pattern within them. That is important.


