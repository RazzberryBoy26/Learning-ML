# Overview:
Would like to share my experience regarding implementing the algorithm for stochastic gradient descent. Learned a lot of new things from the project. It was a fruitful session.

# Some mistakes, and what I learned from them:
1. First set the learning rate to be too high, saw it resulted in nan or inf values. Or just not at all accurate convergent points. A good learning rate is essential to get a fair convergent value.
2. That didn't solve the issue either :,). The problem lied in the fact that the learning rate caused high variance over iterating through each epoch, making each move of the theta vector rather random.
    ## A brief explanation:
    The explanation can be given by the fact that the "noisiness/randomness" of the movement of theta vector is heavily dependent on the magnitude of learning rate. If the learning rate is kept constant and not decreased as we go on, the variance over iterations through all epochs will remain constant and large, causing a huge number of steps to be required for theta to converge, since overshooting will be prominent. I solved the problem by decrementing the learning rate after each epoch by a factor of 0.9 (calling it the decay constant for now), which caused the vector to settle at a good global minimum point in the hyperplane.
3. Learned how to play around with a particular row or a column of any given matrix, since row vectors are required to compute the gradient in sgd.
    
    ## Some observations:
    1. Made a graph between the first and second parameters theta_0 and theta_1. Found the overall graph to be a bit jagged and rough. This is in line with how stochastic gradient descent is supposed to be a bit random/noisy.
    2. The order (in 10's) for alpha = 1/order (in 10's) of dataset
    3. Order of iterations = dataset size (an approximation)

## Refer to sgd1.ipynb for code.

Thank you for sticking around :)