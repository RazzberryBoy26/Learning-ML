# Overview:
This session was supposed to demonstrate how we can use the normal equations to analytically compute our convergence point for theta vector. However, I also accompanied with this a short project of my own of how we might use the hybrid of both types of gradient descents (stochastic AND batch, aka sgd AND bgd) to get good convergence points as well. Although my previous assumption was that this would be an overall better method, but the results say otherwise.

# What the project is:
1. Since, bgd is a gradient descent method known to be highly accurate at the cost of computation power and sgd is known to have faster but noisy and less accurate steps, I thought of combining the two to get the best of both worlds.

2. Starting with a few epochs of sgd to get near the convergence point as fast as possible, and then using bgd to accurately converge to the required theta vector was my idea. I wanted to reduce the time and space taken for the overall algorithm relative to other pure gradient-descent algorithms like JUST bgd or JUST sgd (which, didn't work really ;-; ).

# My mistakes, and what I learned:
1. For the first few projects that I have uploaded, there was an error in convergence values for some theta features, since, to check theta I only compared theta_0 and theta_1. However upon further inspection, I found that few of the theta_j features still remained far from convergence. This, I confirmed by running a while loop on my theta matrix to print all its parameters. I will not be committing any changes to those files since I believe that making mistakes is one of the parts of learning deeply. Or should I say, Deep Learning. ;)

2. I tried to implement my sgd + bgd algorithm and checking its closeness to analytical values computed by the normal equations. While doing so, I implemented the while loop incorrectly for sgd such that it was only getting through 1 epoch pass. Fixed that after seeing the quality of values.

3. Upon implementing the two as a hybrid, I found that the convergence values for a few theta_j features were still far off from the convergent point. Upon playing around a bit with the learning rate, the number of iterations and the number of epochs, I discovered that the iterations for bgd in the hybrid algorithm and for those in pure bgd were actually equal, with slightly less accuracy on the hybrid one. Although both converged pretty well, the main goals were not met.

    ## Since the hybrid algorithm failed to complete its goals, the main purpose of the project was defeated ;-; . However, there were a few takeaways:

    1. I feel the problem might be with the fact that for "normal" sized datasets, the algorithm will fail to save space or time complexity. But for huge datasets, this might actually be useful as the number of iterations through each epoch will increase, causing the theta vector to essentially move towards the convergence point.

    2. Why not with "normal" sized datasets then? 
        1. For normal-sized datasets, the noisy steps may actually setback a few parameters instead of getting them closer to convergence.
        2. Then, when we apply bgd, our convergence may not be as good as pure bgd, since few parameters have become farther from the convergence point than our initialised parameter (theta = null vector), when bgd started.
        3. When we increase the size of our dataset, one pass through the dataset will cover many examples and the overall variance/noise, being inversely proportional to the number of data points in the dataset, will essentially decrease, leading to less noisy steps AND yet faster convergence, hence accomplishing our main goal.
    
# A few interesting observations:
1. For a given convergence point for the theta vector, if we keep the product (no_iterations * learning_rate) constant with some set of values, we get approximately the same result for any other set of values that satisfy the equation. This might only be the case with MSE cost function only, but would like to see if this works with other cost functions as well.

2. Basic graph drawing between theta_0 and theta_1 shows how the parameters first noisily approach their convergence point, then take a stabler path towards the point, as expected from an initial sgd + finishing bgd combination. This is the case with nearly all graphs.

3. The SGD + BGD dataset took approximately 4 seconds to execute (for california_housing dataset) whereas the pure BGD one took 2 seconds. 

Thank you for sticking around :))