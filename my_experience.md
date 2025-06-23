# Overview
I would like to share my experience with everyone whilst doing the implementation. I learned quite a few things along the way- either by making errors, or just plainly meditating on the concept itself. I also had a few ideas to implement with the algorithm so as to make it more robust/accurate/fast, which I would also like to share.

# Some mistakes, and what I learned from them:
1. Thought of implementing the whole algorithm without using tools like matrix operators. I run whole loops through matrices and operated on each individual entry. This was a mistake, as operating on each individual entry proved to be a timestaking task. Hence, just used the simple '@' symbol to multiply matrices. Process became much faster.
2. Many times entered the wrong matrix dimensions during operations. This'll go away with practice I guess ;-;
3. STANDARDISATION-SCALING IS KEY. Running the algorithm without scaling the features of input matrix X can cause the whole result to blow up. Convergence will be negligible and inf or nan values will result. To fix this, scale the features down/squish them between the values of 0 and 1 using this formula:
    ## X_scaled = (X - X')/(S);
    Where X' = mean of all entries of respective feature, S = standard deviation of all entries from mean of respective feature.
    There is a library called StandardScaler in sklearn.preprocessing that can be used for this.
    This was something that I could've learned only by implementing the algorithm manually. And yeah I spent something like 1.5 hours trying to fix this ;-;
4. Playing around with the learning rate and the no. of iterations was something that took up the majority of my time. Finding that sweet spot for the correct convergence values is integral to the process, and can only be done by selecting the suitable values of alpha and no. of iterations. 
    ##  A few interesting observations:
    1. The order (in 10's) of no. of datapoints was equal to the order of no. of iterations so used.
    2. The alpha so selected was then 1/(the order of the no. of datapoints).
    I'm not sure what this might mean, but would try to see if this observation holds out with other linear regression suitable datasets as well.

# A few ideas:
1. Is there a way to bound our convergence point between some given values? I feel this might be possible using partial derivatives and some more calculus. Will try to come up with an algorithm for the same.
2. Can I speed up any gradient descent algorithm by first implementing SGD(Stochastic Gradient Descent), then implementing BGD(Batch Gradient Descent)? The first few steps being noisy but fast approaching the convergence point, the next steps being more accurate, stable and closer to the convergence point. Will try to implement this as well.

## Refer to bgd.ipynb for code.

Thank you for sticking around :)
