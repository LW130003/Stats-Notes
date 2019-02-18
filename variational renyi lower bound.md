https://www.inference.vc/variational-renyi-lower-bound/

Why do we need variational lower bounds?

One way to define a probabilistic generative model for some variable x is via latent variables: We introduce hidden variables z and define the joint distribution between x and z. In such model, typically:
- p(z) is very easy
- p(x|z) is easy
- p(x, z) is easy
- p(x) is hard
- p(z|x) is very hard
to evaluate.

Unfortunately, in machine learning we need to calculate are exactly the bad guys, p(x) and p(z|x)
- Inference is evaluating p(z|x)
- Learning (via maximum likelihood) involves p(x) or at least its gradients.

Variational Lower Bounds gie us ways to approximately perform both inference and maximum likelihood parameter learning.


Standard Variational (VI) Lower Bound

To nice auxiliary distribution q(x,ψ) 🦄, that is both easy to evaluate analytically and easy to sample from, and define the lower bound as follows:

L(x,θ,ψ)=logp(x;θ)−KL[q(z;ψ)∥p(z|x;θ)],
where θ are the parameters of the generative model. Hey, but doesn't that formula have the two things we can't evaluate? The good thing is that the lower bound can be rearranged to a form where we don't need either of those:

L(x,θ,ψ)=Eqlogp(x,y;θ)q(x;ψ)
So basically:

log(🦂)−KL[🦄∥🐉]=E🦄log🐨🦄
so we only have to deal with koalas and unicorns. Sweet.

