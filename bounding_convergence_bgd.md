# What I aim to do:
The batch gradient descent algorithm requires setting a suitable combination of the number of iterations(n) and the learning rate(α) to get our required convergence point over any convex quadratic cost function. To set these values is generally a matter of trial and error. Using the proposed algorithm, we may be able to bind the analytic convergence point for any parameter between two values. This allows us to get an estimate of where the convergence point might lie, and henceforth, giving us a rough idea for setting 'n' and 'α' suitably. The overall trial and error process will be sped up many fold.

# Important assumptions:
1. The cost function J so chosen, is convex.
2. It has a single global minimum to move towards.

# The Algorithm:
1. Consider any one particular feature of $\vec{\theta}$ vector, $\theta_{j}$ ​. We initialize $\theta_{j}$ = 0 $\forall$ j $\in$ [0, N], where N is number of features. Our basic updation algorithm remains the same, that is: $\theta^{t + 1}_{j}$ = $\theta^{t}_{j}$ - $\alpha$ $\frac{\partial J(\vec{\theta}^{t})}{\partial \theta_{j}}$, where 't' is the sequence counter.

2. Since the cost function J($\vec{\theta}$) so chosen is convex and has a single global minimum, our updation shall take place monotonically in the direction of our analytic convergence value, i.e. the value of $\theta_{j}$ will either monotonically increase or monotonically decrease with increasing t.

3. Considering the purpose in hand, I would like to speed up the process for selection of '$\alpha$' and 'n'. Let's initialise 'n' and '$\alpha$' with some arbitrary values. Upon setting these up, there can be 3 possible cases:
    1. The $\alpha$ and n are too small to approach the limit, sluggish movements are seen with each t.
    2. The $\alpha$ and n are too large to approach the limit, movements oscillate with large amplitude around the convergence point with each t.
    3. The $\alpha$ and n are very much suitable to approach the limit, and good convergence is seen with each t.

4. To get an interval matrix which contains the limit for $\vec{\theta}$ vector, we consider the direction of approach/the trajectory of $\theta_{j}$ $\forall$ j $\in$ [0, N] individually. Plotting a graph between sequence counter t and $\theta^{t}_{j}$, we see that for initial t, the direction of $\theta_{j}$ is monotonic (either purely increasing or decreasing, as established already in point 2).
    ** The direction of $\theta_{j}$ at some t is defined as $\theta^{t + 1}_{j}$ - $\theta^{t}_{j}$ **

5. To find a bound for the limit of $\theta_{j}$, we will find the first occurence of sign change.
    **This matters because this $t = l^{th}$ sequence counter will now serve as our first bounding value.**
    1. **Why the sign change?**
    We know that in the initial phase of the sequence, a monotonic behaviour was observed. But, in the next few iterations it might so happen that the value of $\theta_{j}$ exceeds (if initially monotonically increasing) or goes under the limit point (if initially monotonically decreasing) due to a large learning rate. This would cause the $\theta_{j}$ to overshoot the convergent limit. However, since the sequence ultimately converges to the limit (mathematically proven), it would cause the direction of $\theta_{j}$ to change sign, to again "try and go back" to the convergent point. This will give us one bounding value for the limit point.

6. To find the next bound after this, we will have to find the next occurence of sign change.
    **This next occurence at $t = r^{th}$ sequence counter will now serve as our second bounding value.**
    1. **Again, why the sign change?**
    If the second sign change is observed, it means that again $\theta_{j}$ overshot the convergence point. Which means it would cause the direction of $\theta_{j}$ to again change sign and "try and go back" to the convergent point. This will give us another bounding value for the limit point.

    2. **Why the second occurence?**
    After the first occurence, the second occurence will change the sign back to the original sign, causing an overall oscillatory behaviour around the convergent limit. The bounds of these oscillations will serve as our bound for the limit point.

7. These two values will serve as our upper and lower bounds on the convergent limit. To view a graphical explanation, click here -->[].
**Note : X - axis denotes t(sequence counter) and Y - axis denotes $\theta_{j}$.**

8. Now let's go through each case given in point 3 and see what happens:

    ## Case 1. The $\alpha$ and n are too small to approach the limit, sluggish movements are seen with each t.
    1. This means that the sign change will never occur in the first place, as $\vec{\theta}$ is approaching the limit point very slowly starting from $\vec{0}$. Hence, possibility of overshooting the convergent point at all is negligible.
    2.  This means that no sign change will occur. Hence no upper bound is obtained. This will give us an indication that '$\alpha$' or 'n' might be too small, prompting us to increase it accordingly.

    ## Case 2. The $\alpha$ and n are too large to approach the limit, movements oscillate with large amplitude around the convergence point with each t.
    1. This means that either 'n' is set too small relative to '$\alpha$' or '$\alpha$' is set too large relative to 'n'. This would cause $\vec{\theta}$ to oscillate violently about the convergent point. 
    2. This would be seen by the size of the interval as recorded by the algorithm. If the size of the interval is very large, it demonstrates a larger range for the convergent point. For our purpose, we would want the convergence range to be as small as possible. If we decrease '$\alpha$' or increase 'n', this will be possible.

    ## Case 3. The $\alpha$ and n are very much suitable to approach the limit, and good convergence is seen with each t.
    1. This would mean either a very small or no interval has been formed. Hence, convergence is at par with the limit point.

    ## Case 4?? There are more than two sign changes in the overall sequence formation.
    1. This would mean that $\vec{\theta}$ overshot the limit point more than twice. If the overshooting is more than twice, then a more accurate bound can be formed by the next possible sign changes; since with each iteration, the difference between the sequence and the limit becomes less. 
    2. This would mean, we want to find the last possible pair of iterations with sign changing from same to opposite to same. For this, we will run an O(n) while loop, whilst trying to record the possible pair combinations, and updating them if needed.

I haven't yet implemented the project and would share the code upon finshing it. Nevertheless, thank you for sticking around :)

