Probability concepts explained: Bayesian inference for parameter estimation.

https://towardsdatascience.com/probability-concepts-explained-bayesian-inference-for-parameter-estimation-90e8930e5348

Objective:
- Introduce another method for parameter estimation using Bayesian Inference
- Show how Bayesian Inference can be viewed as a generalization of maximum likelihood and in what case the two methods are equivalent.

Note:
- Some fundamental knowledge of probability theory is assumed e.g. marginal and conditional probability.
- It also helps to have some basic knowledge of a Gaussian Distribution but it's not necessary.

-----------------------------
Bayes' Theorem

Bayes' theorem gives us the tools to use prior knowledge about the likelihood of an event.

Update prior knowledge with new data and you have posterior probability.

P(A|B) = P(B|A) x P(A) / P(B)

P(A|B) - conditional probability that event A occurs given that event B has occurred. [Posterior Probability]

P(B|A) - conditional probability that event B occurs given that event A has occurred.

P(B) - probability event B occurs

P(A) - prior probability of event A occurs

How does Bayes' Theorem allow us to incorporate prior beliefs?

What is the probability of selling ice cream on any given day given the type of weather? P(A= ice cream sale | B= type of weather)


-------------------------------------
Bayesian Inference

Inference: In statistics, inference is the process of deducing properties about a population or probability distribution from data. For example, on maximum likelihood. From a set of observed data points we determined the maximum likelihood estimate of the mean.

Bayesian Inference is therefore just the process of deducing properties about a population or probability distribution from data using Bayes' theorem.

Model form of Bayes' Theorem

Given data, parameter \Theta is what we're interested in. For example, if We're trying to estimate the parameter values of a Gaussian Distribution. Then \Theta are \mu and \sigma. Mathematically \Theta = {\mu, \sigma}

P(\Theta|data) = P(data|\Theta) x P(\Theta) / P(data)

p(\Theta) is the prior distribution. It represents our belief about the 

P(\Theta|data) is the posterior distirbution. This is the distribution representing our belief about the parameter values after we have calculated everything on the right hand side taking the observed data into account.

P(data | \Theta) is something we've come across before. If you made it to the end of my previous maximum likelihood then you'll remember that we said L(data; \mu; \sigma) is the likelihood distribution (for a Gaussian distribution). We'll P(data | \Theta) is exactly this, it's the likelihood distribution in disguise. Sometimes it's written as L(\Theta; data) but it's the same thing here.

 Therefore, we can calculate the posterior distribution of our parameters using our beliefs updated with our likelihood.

 This gives us enough information to go through an example of parameter inference using Bayesian Inference.

 ----------------------------------------
 Why did I completely disregard P(data)?

 Well apart from being the marginal distribution of the data it doesn't really have a fancy name, although it's sometimes referred to as the evidence.

 Remember, we're only interested in the parameter values but P(data) doesn't have any reference to them. In fact, P(data) doesn't even evaluate to a distribution. It's just a number. We've already observed the data so we can calculate P(data).

 In general, it turns out that calculating P(data) is very hard and so many methods exist to calculate it. 

 The reason why P(data) is important is because the number that comes out is a normalizing constant. One of the necessary conditions for a probaility distribution is that the sum of all possible outcomes of an event is equal to 1 (e.g. the total probability of rolling a 1,2,3,4,5 or 6) on a 6-sided die is equal to 1). The normalizing constant makes sure that the resulting posterior distribution (I should really integeral because it's usually a continous distribution but that's just being too pedantic right now) is equal to 1.

 In some cases we don't care about this property of the distirbution. We only care about where the peak of the distribution occurs, regardless of whether the distribution is normalized or not. In this case many people write the model form of Bayes' theroem as 

 P(\Theta | data) \propto P(data|\Theta) P(\Theta)

 -------------------------
 Concluding Remarks

 Why am I always using Gaussians?

 You'll notice that in all my examples that involve distributions I use Gaussian distributions. One of the main reasons is that it makes the maths a lot easier.

 But for the Bayesian Inference example it required calculating the product of 2 distributions. (Messy and didn't go through the maths).

 But even without knowing the math, I knew that the posterior was a Gaussian Distribution. This is because the Gaussian distribution has a particularly property that makes it easy to work with. It's conjugate to itself with respect to a Gaussian likelihood function. This means that If I multiply a Gaussian prior distribution with a Gaussian likelihood function, I'll get a Gaussian Posterior Function.

The fact that the posterior and prior are both from the same distribution family (they are both Gaussians) means that they are called conjugate distributions. In this case the prior distribution is known as a conjugate prior.

n many inference situations likelihoods and priors are chosen such that the resulting distributions are conjugate because it makes the maths easier. An example in data science is Latent Dirichlet Allocation (LDA) which is an unsupervised learning algorithm for finding topics in several text documents (referred to as a corpus). A very good introduction to LDA is can be found here in Edwin Chen’s blog.

In some cases we can’t just pick the prior or likelihood in such a way to make it easy to calculate the posterior distribution. Sometimes the likelihood and/or the prior distribution can look horrendous and calculating the posterior by hand is not easy or possible. In these cases we can use different methods to calculate the posterior distribution. One of the most common ways is by using a technique called Markov Chain Monte Carlo methods. Ben Shaver has written a brilliant article called A Zero-Math Introduction to Markov Chain Monte Carlo Methods that explains this technique in a very accessible manner.

https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation
https://towardsdatascience.com/a-zero-math-introduction-to-markov-chain-monte-carlo-methods-dcba889e0c50

-----------------------------
What happens when we get new data?

One of the great things about Bayesian Inference is that you don't need lots of data to use it.

1 observation is enough to update the prior. In fact, the Bayesian framework allows you to update your beliefs iteratively in realtime as data comes in.

It works as follows: you have a prior belief about something (e.g. the value of a parameter) and then you receive some data. You can update your beliefs by calculating the posterior distribution like we did above.

Afterwards, we get even more data come in. So our posterior becomes the new pror. We can update the new prior with the likelihood derived from the new data and again we get a new posterior. 

This cycle can continue indefinitely so you're continuously updating your beliefs.

The Kalman filter (and it's variants) is a great example of this. It's used in many scenario, but possible the most high profile in data science are its applications to self driving cars. 

http://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/

------------------------------
Using priors as regularizers

We may be at risk of overfitting if we based our estimate solely on the data. This would be a huge problem if something was wrong with the data collection process. We can combat this in the Bayesian framework using priors. 

Priors can act as a regularizer when estimating parameter values.

The amount of weight that we put on our prior vs our likelihood depends on the relative uncertainty between the two distributions.

https://towardsdatascience.com/the-truth-about-bayesian-priors-and-overfitting-84e24d3a1153

---------------------------
When is the MAP estimate equal to the maximum likelihood estimate?

The MAP estimate is equal to the MLE when the prior distribution is uniform.

Horizontal line. Intuitively it represents a lack of any prior knowledge about which values are most likely. In this case all of the weight is assigned to the likelihood function, so when we multiply the prior by the likelihood the resulting posterior exactly resembles the likelihood.

Therefore, the maximum likelihood method can be viewed as a special case of MAE.
