- 
- **Lecture 1 **(Intro)
    - Artificial intelligence around since 1956, still a young field.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/g0yS9euandH2WRZtceJWTd_bVUf7BS1x06YZlheLJ1nm7RDQRUgXy-oIdq-PcSXfjr6EGYYjTVdXlozWcum0eFiHzqYwd-4rtgzHYmm40tJQRXKKtMKzTEFNzN6G6Q7f.png) 
    - No AI on earth can form a good understanding of "Sleep that knits up the ragged sleeve of care".
    - What is are the three versions of AI? ↓ 
        - One version is **acting like a human**. A test for this being the Turing Test. The Turing test is very hard - a human child would probably not pass it. 
Why would we want humanlike thinking? Perhaps we don't need it to give a reason, only a correct response.
        - Another version is **thinking like a human**. To write such an AI we need introspection and psychological experiments to figure out how people think. We then mimic that process. 
CompSci + Psychology = Cognitive Science
        - The final version is that intelligence reduces to **Rational thinking**. We record facts about the world, and the AI derives the effects of it's actions on the world.
It has obstacles with uncertainty, tripped up with computational complexity, acting fast and needing to act without logic.
    - Agents 
        - What is an agent?―A mechanism which can sense it's environment and act on it's environment.
        - Agent Performance 
            - Any measure of performance is likely to be problem-specific. Additionally, measure of performance can conflict - i.e. an autonomous car want's to reach it's destination as fast as possible - but it also want's to be safe.
            - Why are we usually interested in **expected, long-term performance**? ↓ 
                - Expected: because an AI model is not omniscient. You can't know when you walk into a lecture that the roof will fall - a model that could detect that would be more performant, but not more rational. 
                - long-term: Because that usually leads to a better approximation of what we'd consider rational behaviour. 
        - Environment features 
            -  _Accessible/inaccessible_  environment. Do we have perfect knowledge about our env?
            -  _Deterministic/non-determinstic _ environment.
            -  _Episodic/non-episodic_ : is the agent run in independent episodes. E.g. Chess
            -  _Static/dynamic_ : Can the world change while AI is deciding what to do? 
            -  _Discrete/continuous_ : Infinite percepts and actions.
            -  _Competitive or cooperative_  with multiple agents - is communication required? 
        - Programming Agents 
            - Is there a sensible way to structure an agent?
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AYQBAkORBU5GZQpfO304RPM1zRtBoYinx230thA693z8JVBgVqIVwUqbnDLh6Ys3Lh90MoAtfdUA0pAejfGxOHI8W2lKeydLp4QF80_YIXA4ca5oQFW0GfQqYHSggWcs.png) 
            - What 3 things should an agent maintain in memory about the environment? ↓ 
                - A description of the current environment
                - Knowledge on how the agents actions affect the environment 
                - Knowledge of how the environment changes independent of the agent
            - This requires knowledge representation and reasoning.
            - Additionally, an agent acting towards a goal should have some idea of Planning - thus we might search through the action space to find a plan.
        - Utility-based agents 
            - What is a goal?―A goal is achieved when the environment is in some desired state. E.g. the gold bar is in the robots hand.
            - However, goals are not the end of the story. We can have multiple goals, conflicting goals requiring trade-offs (and utility functions).
            - What are utility functions?―A utility function maps a state to a number, representing the desirability of that state.
            - Maximising expected utility forms a fundamental model for the design of agents.
        - Learning Agents 
            - Feedback from actions are fed back into the description of the effects of actions and the behaviour of the environment.
            - What is the trade-off associated with learning agents?―**Exploitation vs Exploration**: Time spent exploiting found knowledge, vs time spent trying new things that will initially be less effective. **Local minima**. 
- **Lecture 2 **(Searching)
    - Search Algorithms 
        - What four things are required by a search algorithm?  ↓ 
            - A set of states including an initial state.
            - A set of actions (transition function) $$\text{action}: A \times S \rightarrow S$$ 
            - A goal test. $$\text{goal}: S \rightarrow \{\text{true, false}\}$$ 
            - A path cost $${cost}:A \times S \rightarrow \R$$ 
        - We generally want to find a path with the minimum cost.
        - Depth-first, breadth-first and iterative deepening don't generally work in AI. Too many options.
        - Problem solving by search useful for deciding where to place things on chip. 
    - Search Tree vs Search Graph 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jQDVzFxjfnLxwr59_kTcpdNkfhI79BqRexdlpgDETSpAGec_q4H6wE6ng7pST-QGK7_v9t95CH2j4mDEQ2PCeXEPG1aqsbqMVEU54BiBQ4GbO3RZfzBcq37uJWeqXRKR.png) 
        - What's the difference between a search tree and a search graph? ↓ 
            - In a tree, only one path can lead to a given state on a given layer. But a state can appear multiple times
            - In a graph, a given state is only in one node but there might be multiple paths to it.
            - Graphs can have cycles (trees can as well, but they're less obvious - we could keep looping between states) & redundant paths (where multiple paths lead to the same point).
        - What 3 factors are most important for search techniques? ↓ 
            - Whether a solution is found
            - Whether the solution found is optimal/ a good one 
            - The cost in terms of time & memory
    - Basic tree-search algorithm 
        - ```c
expand(s) = {s' | s' = action(a,s) where a is an action possible in s}
```
        - Expand fills a set with possible actions from a state, we then use this to search the tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JhH3CFxBUhdvUzAW5KngcS4wHUbszAiQuxk1-XlPRxhx-OFh0ptOCvEcJhmZ-I5Xk0S-MJauSxuhM_9FjOSsQsjpYrkux13yXRFB1qiiawP2e96_mpWIUhA_bbviF-i0.png) 
        - The search strategy is set using a priority queue to implement **remove() **of the fringe. The definition of priority then sets the way in which the tree is searched. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cycJro62ngUhbO0dLCQaKh3WgYt7oyFt_8yDNdqgAS15VYD8XaDBipMv7AqtqFuSTNK71Ea5xEji3RhJ6EmAiCB927hfHrhuqOvyGrwVeJa4ph6-e3kMZ9xJqaGZLwlz.png) 
    - Graph search 
        - Need to make sure each state is visited once - need to add a closed list and add a state when it is **first seen**. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u-_Kqx75iks16OGcEI7dWMXLc4DA0wGopVPYAdh8luFoevbQaCmwYgAi_GYH9AmA8jlBkclY0Gg_qiuBGVzZ8GQO77755vnVq-oGSguh3H0grKT6lo2ipnQPM3TbUjiZ.png) 
        - The closed list contains all expanded states - can be implemented using a hash table
        - Worst case time and space proportional to the LARGE state space.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3YiCgh5Bm4kjKi8Jl0-Mnejmi6USkpoBcsabo_7nl78GpWcGLl5aiiSaJCUumQv4cBriRbCgZObHEfb-t-5WMFxgVXTycpnwt2WJcu9q-on_4gechXwqBo58KTvN6xVG.png) 
        - 
        - Graph search builds a tree on the graph. Furthermore the graph becomes separated, any path from the start to an unexplored node **has to pass through a fringe node.** 
        - Note that - we're discarding a node the next time it's found, even if the {{new path you took to reach it is shorter.}} We may need to {{modify path costs}} of the repeated state.
    - Performance of search techniques 
        - $$\text{total cost = path cost + search cost}$$ 
Why is search cost a factor?―Problems in AI are at least NP hard, soo searching time becomes a factor. We might choose a sub-optimal solution to quell search time.
        - How do you form depth first and breadth first from tree search?―Depth first when you add the nodes to be explored at the front of the Queue. Breadth first when you add them at the back. Testing them for the goal before you place them in breadth first saves you time, as you then need not search the rest of your current layer.
        - BFS is complete, it's wlil find an optimal path but it's exponential in time **and space**. And space is the main issue. 
        - DFS - not complete for tree search because of loops. Complete for graph search **if the number of states is finite, **but not otherwise. 
        - What is the DFS time & memory complexity for a tree with branching factor b and depth d?―For a depth d and a branching factor b. The memory complexity: $$\text{memory:} \ \ O(bd)$$
$$\text{tree search time:} \ \ O(b^d)$$ (If you know you have to go to depth d)
$$\text{graph search time:} \ \ \text{size of search space}$$ 
    - Uniform-cost search 
        - Change tree search to try and get an optimal solution, while limiting the time and memory needed.
        - What is uniform-cost search?―Tree search with a twist. Uniform cost no longer just distinguishes between goal/non-goal. Tries to pick the best state to explore by using the path cost as the priority for the priority queue.
        - How do we modify the graph algorithm in uniform-cost search?―If the fringe has a longer path to a node than the current path you took (to that same node), replace the fringe node with the lower path cost version.
        - **Uniform cost search is optimal, when we select a node it must have the shortest path to that node. **
It is complete, provided we cannot get stuck in an infinite path.
Costs must be >0 and branching factor must be finite.
        - Is uniform cost search optimal? If so/not, why?―Yes! When we select a node it **must be the shortest path to that node**. 
Because we search in order of path, any nodes that we explore past our goal node would have a longer/the same path length to it.
        - In practise it doesn't work very well. Gives us the idea of an evaluation function - a function attempting to measure the desirability of each state.
    - Heuristics 
        - Why is path cost not a good evaluation function?―It is not directed in any sense, towards the goal 
        - A heuristic function is one that estimates the cost of the best path from any state s to a goal. $$h(\text{goal state}) = 0$$ 
        - This is a problem-dependent measure. We are required to either design it using our knowledge of the problem, or by some other means. 
        - Example route-finding:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/b98xuixLiyExt74HUubIrRpnJ4YC1JdzwsYqQbTMuaPuZ645iCEVOxHM54QMUsSVVbdWVFrHsEhEWlc-FfYNPYS5qJbuK9eBHS4IH-03S0559btAkFsahaZ6wiJy4AF_.png) 
    - A* Search
        - How is A* different from other search methods?―A* combines the good points of using p(s) to know how far we've gone, and h(s) to know how far we have to go. 
We then form an estimated cost: $$f(s) = h(s)\  + \ p(s)$$
Note, we need monotonicity for A* graph search. 
        - What is an admissible heuristic?―One which never overestimates a given path to the goal$$\forall s. \  h(s) \le p(s, goal)$$ 
        - If $h(s)$ is admissible, then tree search A* is optimal. 
        - 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vrTK0VzqRAVvyyTtOXFi2wlgJrpJ2JIXvEPCclAxPSmRbzvX2yAau6J2vDuDiR66gobgGqprmOh6T3s0A2UrWkpDj1xaVOwKU2FzybPQMd80-2VoiPnffkm1SC3ZjsDx.png) 
        - We say:$$f(Goal_2) = p(Goal_2) = f_2$$ 
        - Assume that this goal 2 is less optimal than f_opt:$$f_2 > f_{opt}$$ 
        - If A* is not optimal, then it can find Goal2 before Goal_opt - assume that's the case - then Goal2 is chosen for expansion **before s**:
$$f_{goal2} < f(s)$$ 
        - We then note that:
$$f_{opt} = p(Goal) + 0$$
Then - as the path to the goal is longer than the path to s and h(s) underestimates.
$$f_{opt} \ge p(s) + h(s) = f(s)$$
We can then form the contradiction: 
$$f_{opt} \ge f_{goal2}$$ 
    - A* Graph Search 
        - For graph search the situation is trickier - as we can discard an optimal route if it's not the first one generated.
        - What is monotonicity?―This is a condition on $h(s)$ which forces the  __best path to a repeated state to be generated first__ . 
Note that
$$\text{monotonicity} \implies \text{admissibility}$$
It is always the case (for a monotonic h(s)), that for a state s - a state further down (call it s) has the following property: $$f(s') \ge f(s)$$
 h(s) is monotonic iff it obeys:$$h(s) \le \text{cost}(s, s') + h(s')$$
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cEd7S8V98DK8tRHoWWLjAxgbfYpO1rNc2xEQ80Mtcmsi2K_LIxYB7jCs7sCB2gt7Rzy4DbljlxqMfTFzrkOVrmcVVMhi3PYaUKkQvGowgOQdxHb2hKBXIFM01HBI_6DE.png)
The logic behind monotonicity: If a path through s has a length of at least 9 (shown above) - how can a path through s' - **which is a path through s **- have a lower path cost?  
        - Give a convincing (but not too complicated) argument that A* graph cost is optimal with a monotonic heuristic―Because $f(s)$ is increasing, in order to find a non-optimal path first it would have to have a lower f cost than our optimal path - but that would mean it's the optimal path. Contradiction. 
        - A* is complete with a finite branching factor, and finite positive constant such that each action has a cost at least $\epsilon$. 
        - A* Complexity 
            - Optimally efficient, no other optimal algorithm that works by constructing paths from the root can guarantee to examine fewer paths
            - Still exponential in time and space.
    - 
- **Lecture 3 **(More searching - including Local Search)
    - Iterative Deepening A* Search 
        - Uses a depth first search, with a limit on depth that is gradually increased. IDA* does the same -  __with a limit on f cost__ . 
        - Explain this code![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/acS2baAgT7vMYSUhudd_In4_rkCrDRN-sKDnbv8LtLm0TXiAc_rPx969TIplEx-5pRvMqgSFwdIrS0iiKREvxAKGY-6_twTO6tJvUtNkyCAiYDb6e6h6yy6g2mHp4Imh.png)   ↓ 
            - NOTE - WE ALSO NEED A RETURN ([], nextF) AFTER THE FOR LOOP I THINK - CHECK YT RESPONSES
            - First set nextF to infinity, meaning we don't know our smallest path above our pathLimit. 
            - Then we check if we're currently above our limit, and return []
            - If we're a goal we return our path to us. 
            - Otherwise, for every vertex reachable from us, try and find a path from that vertex to the goal - if the newpath is not [] then we've succeeded and can return.
            - If newpath is [], then we'll try and update nextF.
        - if newPath ≠ [] then we must have found a goal, meaning we can finish. Otherwise, we'll update our nextF.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WCOAvQZQY8XNA5DzcAX2QDF719t-QBoDeM0fB0u9i6X5t7OkngF0tc31pqkcsWvqWTVNlxOz2vaVGJJVtph_v056DFNrmX-24JxWPfHtblM63lYbzadkbeb3WVCugOTI.png) 
        - Propereties of IDA*:
            - Does not require us to maintain a sorted queue of nodes
            - Only requires space proportional to the longest path
            - Time taken depends on the number of values h can take. If h takes enough values to be problematic, we can increase f by a fixed $\epsilon$ at each state - guaranteeing a solution at most $\epsilon$ worse than the optimum. 
    - Recursive best-first search 
        - This tries to use f, in tandem with a depth-first search with a few alterations.
        - Describe recursive best-first search  ↓ 
            - Continually explore the best $f(s)$ at each node you come across. 
            - Store the $f(s')$, the best possible alternative you've met.
            - If you find an s such that $f(s) > f(s')$, backtrack to $s'$ and update any nodes we meet with a cost of $f(s)$ - so we remember the cost of a path so we can easily re-tread it. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9XR8QAG1r5CQY5QYcXrvVCf6bT90dQMPrawc-9SQiyX8hSHPfmPdXXrzRFqFAFXyQwUPFX6DHmNkMe_52Pi5DarxcQy7B_vopkYA5MIHoRS0rnUXATBupjFNE6kyOT8c.png)
What does the $$\text{for each s}' \in \text{expand(s)} ...$$ 
do (the entire for, not just the first part)―This is a solution for a non-monotonic f, if one or more of the states has a reduced f cost - use the older one instead.
        - Properties:
            - Good: If h is admissible, then RBFS is optimal
            - Good: Memory requirements is $O(bd)$ 
            - Good: Generally more efficient than IDA*
            - Bad: Time complexity exponential
            - Bad: Can spend a lot of time re-generating nodes
    - Local search 
        - Instead of trying to find a path from start state to goal, we explore the  __local area __ of the graph, meaning those states one edge away from the one we're at.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YGY2QD1QGEtTRuKQmbAOGnSTE-ZbJKclhA4Eumu3iiEQpHml6zP12hoDbLX8fqi9CZSEJvODgPR-da4JcJgXwTzhsJAMzEzdeYBJsFlOGfgJQkKSnBSAAvYMPwXER1Hv.png) 
    - The M-Queens problem 
        - Take a state s for an m by m board (with m queens) to be m numbers draw from the set $\{1,..., m \}$.
        - We move from one state to another by moving a **single queen **from one row to another. 
        - We define $f(s)$ to be the number of pairs of queens attacking one-another in the new position. 
    - Hill-climbing search 
        - Describe Hill-climbing search―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_UWRwdfqDpsBWbq_SaFcKQGuLeJDz6JGty3SzPiKFYWsSQQY8KtfHeB6UlL-KVzJ6xft41XLz7sGFjRX0zfRLejtYQBs7yXPUC6HnY5S12RigVEHCdga4NZdqBEJu79u.png) 
        - The reality of Hill climb search
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/srmpDAa2DQ5u3Uf96tvrl1qJKebOKlKHA8hSV8D2qoWGLVFd-5cQfbH4WZAsYykpS4ygOm6TO9RKyccASrufZ7tAc772mjXJGKgRvb0MQ9SUfyGdW8tNSqPBcvs68JRe.png)
We can find ourselves in local maxima! 
    - Stochastic Hill climbing 
        - Describe stochastic hill climbing―We still cannot take a step to neighbours with a lower f. However, we make the **probability** of stepping to other neighbours proportional to the increase in f.
Means we can take a "less good" increase in f
        - Beam search: Maintain k states, at each search step find the successors of each and retain the best k from **all **successors. 
    - Gradient ascent and related methods 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AlORArcC5bLSmJ5P_QpQERZ63g_9PCrKtkLIj-gKjlJcrNjG5L-eSkqOmJxjOG9f-4EiUWED2j4RZuwv3Zy-rSfzO7J2LG257-HUTuUEICJ2txeWEu_T8DMltKJXso9V.png)
We have a function $f(\bold{x}):\R^n \rightarrow \R$ and we want to find $$\bold{x}_{opt} = \argmax_x f(\bold{x})$$ 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hfOFzxbCagjstMzLq52SZEuI3yYTTbt0xiLiHPqxLVgfMhc_hLabbWJ0QtqHnHcVZjz1M6K0Na-2IXVBSZhq_Ul5Wl0qT95Sh7jrN6S4vFRYLDARTiuuRYMkDjk_VftR.png)
However solving the equations shown above is not usually **analytically tractable.** Regardless of dimensions. 
        - Describe gradient ascent ↓ 
            - Start with a random point $x_0$ 
            - Continually iterate the following with a step size $\epsilon$. $$\bold{x}_{i+1} = \bold{x}_i + \epsilon \  \nabla f(\bold{x}_i)$$ 
            - Note: If the gradient is negative, move opposite to the gradient. 
    - 
- **Lecture 4 **(Games)
    - Solving games by search 
        - The problem is, the outcome of your actions **are not known **because you don't know what your opponent will do. Makes this a more realistic search problem.
        - Chess is a hard problem - average branching factor of $\approx35$. Games can reach 50 moves per player, rough calc gives $35^{100}$. 
        - In addition, uncertainty due to opponent - we can't find a complete search to find the best move.
    - Perfect decisions in a two-player game 
        - For noughts and crosses, the operators, terminal test and utility function are (respectively)―Add a nought or a cross, check if there are 3 noughts or 3 crosses and whether you've won or not.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YYeSJbR5jNjhZJF8TngrTGVF4qgZn_bwJXJlu_1ihr50hJy7hcojt3vGjf-rLrdD4dG11aYjWl2q7Joeag4ud5Kyd0fY3NZQRqVbUJOT3AIwdZKVbp0pgmfDs3wwQGYm.png) 
        - Give the basic idea of the minimax algo―Max wants to find the biggest utility, Min wants to minimize Max's utility.
So in the minimax algorithm, Max assumes Min will pick the choice to minimize his utility and works from there.
So Max picks the branch which **has the maximum, minimum child node utilities.** 
I.e. the biggest, smallest node as we know Min will always pick the smallest one. 
        - How do you generate the minimax tree? ↓ 
            - First generate the complete tree according the the utility function, e.g. generate all successors and number them. 
            - Work from the leaves upwards, label the nodes depending on if Max or Min will move
            - If it's Max's move label the one with max utility
            - If it's Min's move label the one with min utility.
    - Making imperfect decisions 
        - Cut-off test, instead of using the utility function - introduce an **evaluation function **a function that generates how likely it is Max will win. 
This evaluation function is critical - need some human ingenuity to generate this.
    - The evaluation function 
        - What is a category in an evaluation function?―A set of states where the evaluation function gives the same result for all. E.g. for a simply chess evaluator looking at material, all the states where white is one pawn up.
This is very naïve.
        - We could try and learn an evaluation function, construct a weighted linear evaluation function: $$\text{eval(position)} = \sum_{i=1}^n w_if_i$$
A sum over the weight times the **feature** where the feature could be the value of the i'th piece. 
    - Alpha-beta ($\alpha$-$\beta$) pruning 
        - We can prune the search tree, without affecting the outcome and without having to examine all of it.
        - Explain alpha-beta pruning―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T6kuP9Z_pwRN7nawwWTJf6IX2ewtpE14dD4Ww6DTMeY2cw2xpiAxVw-heMYNMSGfk7H0FPHrEN73PJnVyzVnpEBqw1ysycQORN2yQxFrjMw3XSzT0wyX5-4UAcGtQEJ8.png)
We know Min will choose the lowest one, so no need to search those ones.
So we do left-to-right depth first search, and when we find a node lower than **any node along our (current depth first) path** don't examine it, as there is a better path earlier in the game.
$\alpha$ is the highest utility seen so far on the path.
$\beta$ is the lowest utility seen so far on the path. 
        - Explain this code
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MP76mRUCS0OakVm7HK8tC_rc_LzxZehAcf8E5gRF380f4k1t9tisF1xbZWzRuBzL3MwIryWd_ZMLJapU8h1EGEAg7IPkv8jrlhyqpx6u3807VOAdyeykkKxDtZbm6A4v.png)  ↓ 
            - First we check if the game is over or if we shouldn't search anymore.
            - Then we set the initial value of the position to negative infinity (so any larger value will update it).
            - Then for each successor, we find the max of the current value and the **opponents best move**. 
            - The opponents best move will be the move that minimizes our score at this position.
            - If our new value is better than the worst position the enemies seen so far, stop searching here - as our opponent won't let us get here. 
            - Also update the best value we've seen so far if we need to, this is to inform the enemy to prune elements worse than the best element we've seen so far.
            - Otherwise update the value.
    - Effectiveness of alpha-beta pruning 
        - If you always manage to pick the best moves first, AB pruning would be $O(q^{p/2})$ rather than $O(q^p)$. 
Allowing us to search ahead **twice as many moves as before**. 
        - If moves are arranged at random then: $$O((q/\log q)^p)$$
When q>1000.
For reasonable values of q:
$$\approx O(q^{3p/4})$$ 
        - In practice, simple ordering techniques can get close to the best case. E.g. captures, then threats, then moves forward etc.
        - Transposition table, we're really searching positions on a graph - so we might return to the same position multiple times. Hash the evaluation of the position in a table.
    - 
- **Lecture 5 **(Constraint Satisfaction Problem)
    - Constraint satisfaction problem 
        - Previous methods had issues that  ↓ 
            - States were represented in problem-specific and arbitrary data structures. 
            - Heuristics were also problem specific.
        - So we would like to transform general search problems into a standard format.
        - CSP standardises the manner in which states and goal tests are represented. Meaning we can develop general purpose algorithms and heuristics.
        - What are the 3 main components of CSPs? ↓ 
            - Variables $V_1, ..., V_n$ 
            - For each $V_i$ a domain $D_i$ specifying the values that variable can take. 
            - Constraints $C_1, ..., C_m$, involves a set of variables and specifies an allowable collection of values. 
        - A state is an assignment of values to some or all variables.
        - An assignment is consistent if it obeys all constraints
        - An assignment is complete if it gives a value to every variabe
        - A solution is a consistent and complete assignment.
    - Node colouring Problem 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3l8fQv2tGPXrLOZU9t51TnPgwEDH0R_8IZ8CWZk6isR-z92NUiFrYHisTrckhYDUTHL2QRnXfE-_cALNC3aIleTjiDgkVCYUuiNr55x375DpWMr7OzzL7iTnDInujZc6.png) 
        - Variables are the colour of nodes, constraints are relationships between nodes sharing an edge. E.g. certain nodes cannot have the same colour. And the domains are {B, R, C} - black, red and Cyan.
        - We'll deal with binary constraints. Higher-order constraints can be considered, but when dealing with finite domains they can always be converted to sets of binary constraints by introducing extra auxiliary variables. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-O8DxnSGI0CtFnfzKONj5dRyctXXh5Qpc6zs8DevZvnzemNjN8t_HwUIjBYwiBIitoj2YXl62WVqCxd35le1FZrwtws3adVRbWafyv5TCM6aZjZYDOQ1wKyXl7X3CAal.png) 
    - Backtracking search with CSP
        - We can very simply do a backtracking search, where we assign variables at each step - and backtrack when an assignment would violate a constraint.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-QsFRWZH3ykZ48Zum0XMW137bW8q-_QAG6M4XVK9y1ZZHROJ7tpb_bBH2HRYEkZcMgrzaXos3CH5gOvibS2c0PLbZHEO8pSqzSJqww_lF6_xqvUwfZe0NCNn8O-9jagP.png) 
        - Note that choosing the {{next variable}} to assign is subject to a heuristic. Similarly, the {{order}} that we'll try and assign the variables can be subject to a Heuristic.
        - What effect might the values assigned so far have on later attempted assignments?
When forced to backtrack, is it possible to avoid the same failure later?
        - Can we try and force failures? 
        - Describe the minimum remaining values (MRV) heuristic―We choose the variable with the smallest available domain, so we fail earlier on.
        - Describe the degree heuristic.―Choose the variable with the greatest number of constraints, to get things started and so we can make the big failures early.
        - Describe the least constraining value heuristic.―Choose the variable which constrains other variables the least.  
    - Forward Checking and Constraint propagation
        - Describe forward checking and contrast against constraint propagation ↓ 
            - Forward checking means when we assign a value to ourselves, we also remove that value from other variables (that we are constrained withs) domain.
            - Constraint propagation uses forward checking, but also checks the values of the other variables - to check if their domains are now in conflict with their neighbours and they can no longer be satisfied.
        - Arc consistency 
            - Consider a constraint as being directed - i.e. $4 \rightarrow 5$. 
            - What is arc consistency?―If we have a directed constraint $i \rightarrow j$ (where i and j are variables), and the domain of i is $D_i$ and j is $D_j$.  
i and j are consistent, if for every variable in i's domain - there is a possible value in j's domain so $i \rightarrow j$ is valid. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Hdb0h41giFp-RIsGbSmgPxJ3dc7x-R-1vH6KDO3b_XZIfxTCCl-qCTTnOfD1GPbsUXByzy-Zk2Hzq-OqAOUuofn-mQfDihE_0dycn7NywkrwN7zKmXxRRgMbzAujAErS.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/R2gvLTpufGR6BjNFgaSvLEGOwUiIUMS4gHLLT4A5wPnZyDqSHjkVVONuojzW7bLdp8ArR9nK_taCwcbsHgHbqoVLZvMgPPs5bCHo23elWPXfgqChivmJTsNs6PchxBfX.png) 
            - In order to maintain arc consistency, what do we need to keep track of and why?―We need to keep track of a collection of arcs to be checked, because whenever we alter a domain to achieve consistency - we might be making a previous arc inconsistent: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jwREi0peRfLfe55kf3CRP0KiLPCXn1N24KNuqjUuohZcj7AW9kQe-2bqGrcYaLvy4N8sUvf9fW0fNjcnFm9ynL7w596X3_kMGYuq5crcoUzP1t-MBEbOZUkx_uHkrCTE.png)
So we would need to filter down and check all consequences - we're just backtracking... 
        - The AC-3 algorithm 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KGvBIGCEgwNDkOsSZP0kvMBVGVD_arVEPVsINW-orSB5ulC7wF99An6BkUijyjWLFHhatAtak5z-4C7ebmq8x6kiJBkMj8VLIxFKrJRoDd--MZgoTNLsOa1JWnOnsZHg.png)
Describe this code―We just check if there are inconsistencies, if there are then we need to check all the neighbours. Otherwise keep on truckin'.  
            -  _Complexity_ 
                - We've likely done a bunch of deletions at each stage, reducing the size of the search tree. 
                - Note a binary CSP with n variables can have $O(n^2)$ directional constraints. 
                - Any $i \rightarrow j$, can be considered **at most** d times where $d = \max_k | D_k|$ because only d things can be removed from $D_i$. 
                - Checking any single arc for consistency can be done in $O(d^2)$. 
                - So the complexity is $O(n^2d^3)$. 
    - More powerful consistency (k-consistency)
        - k-consistency: Given any k-1 variables and any consistent assignment to those,  __can we find a consistent assignment to any __ $k^{\text{th}}$ variable? 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nXUHK8AWtIkKlwjd2Rt_PF9gtd-n7j5pFOuGprHKjWQfUjL7cPUzALmP8dU4UtUxwJQhaDDfAYjjSMAecl2g4l9ka3ow2ABNd6HOzpZKRkGm4NCm5JXwX75S6dKKsBzV.png) 
    - 
- **Lecture 6 **(Backjumping in CSPs)  
    - Backjumping 
        - The basic backtracking algorithm backtracks to the most recent assignment, this is called chronological backtracking and is not always the best method.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/P6BieF_pJobtGcxzqp7lKnIPTboSDBslxoTJBqhIqFkKJZiK_PA407wKhhDQz3FBVPWDiPfFQ1PEvWOIk2F7aYFRbd45g3uVaUtTiqqU2ahKRCr8K7MOfJyOxbHGmob2.png)
Clearly ^^ trying to reassign 4 will have no effect, we would rather jump back to 5. 
        - Graph-based backjumping  works as follows: on  attempting to assign to a  variable V for which no  consistent assignments are  available we backjump to the  most recently assigned  variable that has a constraint  involving V.   
        - Notation:
            - Assignment: $A_i = (V_i \leftarrow d)$
We set our variable V to some d in the domain. 
            - Partial instantiation: $I_k = \{A_1, A_2,...,A_k \}$ is a consistent set of assignments for the first $k$ variables. 
            - Conversely, $I_k$ conflicts with a variable V if no value for V is consistent with $I_k$. 
            - We shall assume that variables are assigned in the order $V_1, V_2,...,V_n$. 
    - Gaschnig's Algorithm 
        - Describe Gaschnig's Algorithm you fuck [💯](../💯.md)  ↓ 
            - When choosing a value for $V_{k+1}$ we need to ensure that the candidate value $d$ doesn't conflict with $I_k$.  
            - If there is a conflict (as there is likely to be) we must choose a different d. We record the most recent assignment $A_j$ for which there was a conflict. E.g. We note down which variable in $I_j$ conflicted with $V_{k+1}$! 
            - If we can't find a consistent value for $V_{k+1}$ with $I_{k}$ then we work back to $V_j$ - looking for the smallest $I_j$ where there is a conflict with $V_{k+1}$$$j = \min \{j \le k \ |\ I_j \ \text{conflicts with} \ V_{k+1} \}$$
E.g. EARLIEST NODE IN $I_j$ WHICH CONFLICTS WITH US. 
            - If we find no such values, we revert to backtracking chronologically 
    - Graph-based backjumping 
        - Can we do better than chronological backtracking after we find a conflict?
        - Given $V' = \{V_1, V_2, ..., V_k \}$, what does the ancestors of $V_{k+1}$ mean? And what does the parent mean?  ↓ 
            - Ancestors are the subset of $V'$ that are connected to $V_{k+1}$ by a constraint. 
            - The parent is the most recent ancestor of $V_{k+1}$. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UMhc3E-DBfhxkY6ZyNB2VxLP7cmGZtJMmzbPR7V1JhqTuhffEPczOwxrOWnqJ6jmb1MbCa53-iuOtvjMbmfOMagk4JhhzdP6YC9qhIR-YouNU7dOb5uJafDAhgFD-Iht.png) 
        - Why shouldn't we just jump back to a parent variable every time there are no assignments left?―If the parent has no other instantiations, then we then have to jump back to the parents parent - **but **crucially there might be an easier way to fix our variable, e.g. via v3 below.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uBqxiR83zlDYqezhboHLuer-0jfMTNBTn2WQGCBJZCuQO0wkLFjTFD_A8o3DDqUttK9bZluB0OyC0_QhG2X6FipA2SLy79FuZIJqrLiZ5q_cEfjurncQqU8EyC1MkFeq.png) 
        - What is a leaf dead-end variable and a leaf dead end?―A lead dead-end variable is a variable with no possible instantiations left. A leaf dead end is the partial instantiation of variables with a leaf dead-end variable.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KcBnFaBcV5rwJfO2lWiEG91tDP0eavEpdimNKqYpaqKmluf9NWOBqqlJ299TkEHrygA6AH3OUvQvt5fv6AQRxanikYplaiqr-TBkobpz31KpZDYTYTYkFtO4sagBZ2BI.png) 
        - What are internal dead end-variables and internal dead-ends?―If we backtrack from a leaf-dead end and we have no more instantiations - that's an internal dead-end variable. We call instantiation the internal dead-end.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OZ2ZVcYNRwvBATnAeMUbqPdxVNhcV4wtZwLEe8ImwaB9jeUj9ST55Fz3yabyLK5CnB6Lk-xFt6cmhyjDqxzPGonYLopXVzuJog91WWWXHQWaiCHrUVNBl_HCuSInIhFk.png) 
        - The session of a variable $V$ beings when the search algorithm {{visits it}} and ends when it {{backtracks through it to an earlier variable}}. 
        - The current session of a variable $V$ is the {{set of all variables visiting}} during it's session. This session will contain {{V.}} 
        - The relevant dead-ends for the current session $R(V)$ for a variable $V$ are―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/olzkhNnjWgyjb5GLAJ0agwWwoa51A6rm71m4antz0c247FYYaCbpq8Lek0kOTmmr0XGfw6-Rma8E20gOi4f8tE-4IXb-tkmp698Y-zbWgQxjL0TQYDyIfZvRDWtmceBU.png)
We accumulate all the dead ends in our session. 
        - Say $V_k$ is a dead-end, what are the  __induced ancestors __ $\text{ind}(V_k)$ of $V_k$ - in words or with maths ↓ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hWvapoDX0308gphwK935Ev_D_08Xkh7Cqp5u68O5qcDUTMQ9bK2frycZAWMTBXGfpLuZrzi0H05snpgSX8hbrdi5n8dvIvU5aO6IzG5fDVrJvImbEJBASw5f5TvAKYeb.png) 
            - All the nodes before $V_k$, intersected with the set of all ancestors of the relevant dead end nodes. E.g. it's all the nodes before $V_k$ that are connected to a dead end. 
        - What is the culprit for $V_k$?―The most recent node in $\text{ind}(V_k)$. E.g. the most recent node that's connected to a dead end. 
        - What is graph-based backjumping?―We jump back to the **culprit **for $V_k$! 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i-dfz9O2Qi87pxapxusjLr7uDuPz1rseXxz4TT_0YxW_8xyQK2AE0IM1RB8k5S1l7tcVa8VIVhc0-KxyGgRnblG19WHV11GSN4XIRIVIV9X7znlhDnXOKPC-mFMLgoDO.png) 
    - Varieties of CSP 
        - There are CSP's beyond finite CSP's. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jaytuhmdyT-sy4nPSydv3QqBRysdVTHBYTWgVs9dkkxHrJC6UgPcwf7wes88yXHeJO6AcZlQqdL9H0md_J0Q9FlQ8XmJphLjvdYXMpU6GlljSy7H2wwaPIXX9bVT4AyT.png) 
    - 
- **Lecture 7 **(Knowledge rep and reasoning 1) 
    - Knowledge Representation and reasoning 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LBb7i-_3rCY5wuDE_-3mD-eW6Dn3EM-RRNydd8A78Hv_FrUmWh68-ejiZi4yM42EHYEBP87FaDmFurnuNZFdGIgEwyrmO3MP7hB2Q5Wf2IpRuJS2MHUsBsOiYQT3wN32.png) 
        - First-Order-Logic seems a good way to represent the required kinds of knowledge - it is expressive, concise, unambiguous and can be adapted to different context. It even has inference procedure, although it is semi-decidable.
    - Logic for knowledge representation 
        - FOL is good for talking about things like set theory, but more complicated for representing real life situations.  
    - Wumpus world 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fspmnLmNVfylPmb2GALwKQB1tV40WlaTylZyckubjvXa2X4mZAnAghcXVfOtNEenYn_ccquA6iEFd60jzWtg9uqA3TLVuvupmrsYKJ5XfU-GmC1eJAf1AHQW3triDyTU.png) 
        - Cave contains pits. Cave contains Wumpus. Wumpus itself never falls into pit. 
        - If the robot is adjacent to the Wumpus, it can detect the Wumpus.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uwCxBfGEt3_hnkC2ZUjpVFUYYNf7AjHPkZXfVPDOdBHu1TDeDhfJHRdwmGD8eCm-DB5nPEfu2reCdrB0mBazcayCuQmyycDJLiOrpsvkqkVBNVudZ9v_ioKEjkZhcqOT.png) 
    - Logic for knowledge representation 
        - We want to construct a knowledge base, containing a collection of statements about the world expressed in FOL. So that useful things can be derived from it.
        - We want to generate sentences that are true, if the sentences in KB are true. 
        - What does KB entails $\alpha$ mean?―$$\text{KB} \models \alpha$$
This means, if all the statements in KB are true - then so is $\alpha$. 
        - What does $KB \vdash_i \alpha$ mean? What does it mean for i to be sound or complete? ↓ 
            - That means alpha is generated from KB using an inference procedure i. 
            - $i$ is sound if it can generate only **entailed **$\alpha$. 
            - $i$ is complete if it can generate any entailed $\alpha$. 
    - Prolog 
        - How does Prolog relate to knowledge representation?―When writing a Prolog program, you are generating a knowledge base. The Prolog program is the KB, it expresses some knowledge about lists. The query is the inference rule that derives new knowledge.
List notation is nothing but syntactic sugar for FOL - [1,2] = cons(1, cons(2, empty))
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/o4b2SwjuaYo8aaL2qNODZzGjUr2Ukx4N9UFXwtR6cg2kk4PgNX_A-Vt3R6TuDW8NeDePkyH4EzwJdrnI7do9xLSgWxqzgfzgeZimaznL2qze_bb_NG9UoWBKDgZeWzsu.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HVA62ZQkRHO52b7QLstAr7DA-Lq9wvHvUlZyx0Og5iqv7upRq6HrIDt2DCUOviZVnAn9qqUprKP1nZNSg-Bh_UHyma-CGtlMuIb5IJbvMV81mqCUI5UnNIQWZ001iy7z.png) 
        - What does Prolog try and prove if you pass it something like![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xBtSH9EYBY6O8Xfgh8KZRuXZ367hvrfxp4kWgbWIoXBKVQQ4JIvSVCgbeHBvnoQ1b8kzte3tiMRZsakniCLczx81T30gABgxdtbayqiASNouZPiFFqKvwRfT7ml5KVct.png) ?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BeKtOGdvxxVAj0G3RpvVJzgdwE7nUKowCRioNSni46qxGbrvNKieFuCZCNrTavHJUJtvZ7pF6lcE5KMOPJhKDHkq8MbUdLQxAnErmvyazPOOAfjOoUEoAIGnqvAWaeps.png) 
        - Prolog: Restricts you to using Horn clauses, its inference procedure is not a full-blown proof procedure, it does not deal with negation correctly.
    - The fundamental idea 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/515qGn4vvlOWgyY4c4aCyFvkccoIUiv3bVftDq3tIyL3wZaWBR5DjlSVzXfNUHiFNfw0C4_vOWDvcda_lVzh-9D53TMbUbUN5V4acuTqZBm4rVInCtWSn4rqujDz7Kjs.png) 
    - 
- **Lecture 8 **(Knowledge rep and reasoning 2)
    - Situation calculus 
        - The world consists of sequences of situations, over time agents move from one situation to another. Situations change as a result of **actions**. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fhixOcvcxy3Qkr9o0MDVlPAlkCJifc556vaPQHFgJNdMu8M17kliQyHvCWlBre1eVVaEWvrdwPFoZvNj95jp-6UpIQ4XkvWjLO_6-dslcMuP0WkTUc6R4GhZR0Lp1pds.png) 
        - We have a function $\text{result(action, }s)$ which returns the new situation which occurred as a result of that action.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F3_gPqmJPxKU7mZoqwvMOqO3W5Rebo9fhvmcELbNKdCdopnqwwwnqRWUBgglhYB3q4WcELccIylSHN6gUksVAylPagkPBRS6p03mREazUk5hBXJMcwDM6C2LuHRzfA2B.png) 
        - **Axioms I: Possibility axioms**
            - What is the Poss predicate? What are possibility axioms―$$\text{Poss(grab,}s)$$
This denotes that an action can be performed in situation $s$. 
We then need possibility axioms that decide if an action is possible:
$$\text{at(l, robot, s) } \land \text{at(l, gold, s)} \implies \text{Poss(grab, s)}$$ 
        - Axioms II: effect axioms 
            - Describe **effect axioms**  ↓ 
                - These specify the properties of the new situation, that results from an action.
                - $$\text{Poss(grab-gold, }s) \rightarrow \text{Have(gold, result(grab-gold,}s))$$ 
                - These model the way in which the world changes.
        - **Axioms III: frame axioms**
            - Describe **frame axioms** ↓ 
                - Frame axioms describe the way in which the **world stays the same.** 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q3QQW5z4c2TFkmUd9KOGuOvqLHb2kx4UV6AzTSrYfAZ1NMGiIf_Hg0vwF_TH8d7H21_X8AWoG_PvOYHiaMdQEl6bJ91qpD_euUbE4asweQfQjEWk1hnGLz5tapZV94Z4.png)
If I don't discard an object I still have it in the result. 
        - What is the frame problem?―Representing everything that doesn't change when I take an action can take up a lot of space.
Huge amount of frame axioms.
        - **Successor-state axioms**
            - Describe successor-state axioms and how many do we need?  ↓ 
                - If an action a is possible, then some thing  __A is true__  in the new situation **IFF**
(You did something to make A true **OR** A was already true and you didn't make it false).
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Li_NyKnp3YmGJhNTv3f4JcvEMu7JCPEGRKMGdG7FaV9mIdswe53xbUzpJu2Xac431vOgwcNPXZSAZyaHD31TSvI5k7L1uvNwYdlJbLh9-3H8rKxml27jp6W0h2ldR8fK.png) 
                - We need one for every predicate that can change
    - Knowing where you are (and more!) 
        - We can no easily add more rules. We can keep track of the position in the situation, the position the robot is facing, how motion affects location in axioms etc.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PBqYHZA7d1_tHPhfFJJf77IWOU3LQGxntn1mCb398d-4ZwUA2ZqwvxHUg_xJObnKyIbWmBySXSkXo5VwSx5y3SxW4WQiYjcnkNUyF5mltEPFXauezNtuZms8Jq74fFOz.png) 
    - The qualification and ramification problems 
        - The **Qualification problem: **We are never completely certain what conditions are required for an action to be effective. E.g. turning the key to start the car. 
        - The **Ramification problem: **Actions tend to have consequences beyond what it is intended to achieve. This can be solved by extending successor-state axioms. 
    - Deducing properties of the world 
        - What are causal and diagnostic rules?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZE7p82nr3UQJVFtLEIPEQRp5zJYZK4d5pWfe1fBbOdOFxdiOi0leLqhaZK9clw_UcWFmbhKRb8taTMUPfaglqnIjYiluJLq3QdHN9YSmAm_NK5DPW1_-eJN_4OGNIpuH.png)
Produce percepts VS infer percepts. 
    - General Axioms 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xP3IUlp58SkwaYOwMb6ca2e2I0NkeYmJjBchLDcYD_bZohm-eh9L8oisCb5JlUOkIYOzoULRGGPEMrnd0-ws6J7sFN8qUfPQENn2L5GpVr4cuWMO8w7xa9olUVNah8aF.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/hLsaHK0x7PCxitZ4UsQcilYGJn78SoxAkek_vWmequT2NCzSy6QU-UGcZDdtqX0rKa0uTdHfMARoAmeD_WaZpyadReYNJ0vb02weU-eTuqkzeXAFMDnpVTRKmU4gT6VC.png) 
    - Sequence of actions 
        - What do these predicates define, and how could we use them?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/G2yrqm6R9fixoRMe1S5Y6iiyCiPx9VUnFKDCuWmIXqi3H46fUxXQEHiX-r_T2A5UQd9DSxxTNdwy-EWWBBW5OcDaKJVt1OBBDK2oUSE7EL-xLX5EwRc8yEIubXUW2FRS.png)―These define the results of doing a sequence of actions. We could do the following: ```python
 Sequence(Actions, s_0, s), goal(s).
``` Or in formal logic:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/fQRyIIu92zBaB00ByBX9hSan1yHh6wBu3YW09S_Ogv_s-naR_VPSeS75JD7xNZm3tB4VKj7W7WF4lGGBkooFIE-vsUK2dexcaA5-uUbjndcFg_h7A2MQoGA4cDFfycU9.png) 
    - Frames and semantic networks 
        - We'd like to maintain an **expressive **language while restricting it enough to make inference efficient. 
        - 
- **Lecture 9 **(Planning Algorithms 1) 
    - Problem solving is different to Planning 
        - Consider generating a plan to 'go out and buy some pies': 
            - there are  __too many possible actions __ additionally **many are useless. **
            - A heuristic to rank states doesn't help me ignore useless actions (mow the lawn, have a nap etc.)
            - We have to work out  __how to get the pies __ whether that be, buy them online go to the shops etc (e.g. find a method of search) **before we can start to do it.** 
        - How do we relax our requirements to allow for more flexibility, and reduce the complexity of the search problem. 
    - Difference 1 
        - Planning algorithms use a special purpose language, often based on first order logic - to represent states, goals and actions. 
Actions are defined by preconditions and effects:
E.g. if we want $\text{Have(pie)}$
And action $\text{Buy(x)} \implies \text{Have(x)}$
Then we ought to $\text{Buy(pie)}$ 
    - Difference 2 
        - Planners can add actions, when?―At **any point **at all between the start state and end state. Not just a at the end of a sequence starting at the start state.
E.g. I might determine that $\text{Have(CarKeys)}$ is a good idea - might reduce backtracking later on.
        - So we can search forwards and backwards in the same problem.
    - Difference 3 
        - We solve the frame problem in planning algorithms by―We **assume** most elements in the environments are independent of most other elements.
    - Example plan 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ltnMaagx0VdpWcDQcX2KTnbS2bsTDJ0Gq2rDpVlAnAlfaybS7Ewna_aQsiqb9JYWG48C9c7nAO7bPHahpNnk84AaKy8Sfc7F2zWY0xIpbqOYotkMsIZpsnWbwrFA9-Sp.png) 
        - We start with
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/O8nWQLA9FaOq7E45ypYKNe-zg2VfUIgG8e13qAj2bEkp2o2JEJA0aaw8zKgrUiOjjVwOTQHNeRqNRqHAs1hX71wqBZNMGl5XfVVz-RdFAoOoIISUpOju6Czx4hh6cSQD.png)
We want:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NkJWawCsa4WXhrNOp0cALLEU2jhH0Ai6kSvvm4fxPXAQo-m-swCMNqQYi7sWc6_-dAXWtq3r3zrrQ1_Uj0dIGtSYodFOZk_OdLLM3sqLm1Rb0oAy9D5xwEFoMBdt_1JZ.png) 
        - Note that states are conjunctions of ground literals, they must not include function symbols.
Furthermore, goals are existentially quantified.
    - The STRIPS language 
        - Represent actions using operators:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/a87tgU77Ab3aAcj5uAvvPldMxiEf8ipvNBi7bPAcWmQ4KJVXpqeJer_Cl4_Li2VmC8AsTwsGzBe_kTY2l2ar3LRKqkF5g5BEnP9fJeutX7DnRG7A7WB2Ns6tgmaLBGu7.png)
Where the preconditions are at the top, the action is in the middle and the effects are at the bottom 
    - The Space of plans 
        - We search in plan space - start with an empty plan and modify it to obtain new plans. Incomplete plans are called partial plans. 
We continue this until we obtain a plan that solves our problem.
        - Three main operations on plans are, adding {{a step}}, instantiating {{a variable}} and imposing an {{ordering (places one step in front of another)}}.
        - It doesn't whether you put your right sock or left sock first, so we can reorder steps. Don't have a commitment to order.
        - What is the principle of least commitment?―We don't commit to any specific choice until we have to.
        - In a partial order planner―we only specify some parts come before others, not a specific order. Can linearize in many ways when we need to.
    - Partial order planner 
        - Contains a set of steps - each is one of the operators. 
        - Contains a set of ordering constraints - step $S_i$ must occur before $S_j$. $S_i < S_j$. 
        - Contains a set of variable bindings.
        - Contains a set of causal links or protection intervals $$S_i \xrightarrow{c} S_j$$
. What does this notation mean?―The reason for $S_i$ is to obtain some c which is a precondition for $S_j$. I need to get my keys, to use the keys to turn on the car.
    - The initial plan  
        - The initial plan contains Start and Finish, and the ordering constraint that Start < Finish. No variable bindings nor causal links. 
        - Start has no preconditions, it's effect is the start state for the problem. The step Finish has no effect and it's **precondition is the goal. ** 
    - Solutions to planning problems 
        - A plan is complete if―each precondition of each step is achieved by some step in the plan. AND there is no step in-between which removes that precondition.
        - A plan is consistent if―There are no contradictions in the binding constraints **or **the proposed ordering.  
    - Example of partial-order planning 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/HLxd4YUSD5Z-WVc313ABN4NLSo1igyF6nCKNoPwrHfeYiHQrQr9Wi8tolB49zOFocfx8Gf_-dBMFovtcvYPjoVCkXsiRCzVbQTRwfMjHntfJETn5E1GKLEypweqbXgti.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/AIqMVPboU2Y6vnx3oZqBAcrd9kQAUjipXfJs666jB_q6IXoJfi4q2QRP19Hs4GkyDfa84tAq1fsEENKcXRpxb49WmX2OTRsE_lLPvIPSf_3CP_yBq6DRzcHkkrjZxL8W.png) 
        - We first add a buy action, instantiating y to G in Buy.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BvdnWxUyOiIXnZ09tf9wfpMuKmoh-JC6-Uvl-9I7dtfTneAA24CTkx1WxeR__U_8CI9wKt2xAz-_G5h3MkrAWMzuiI6fH6cBr5pXTjWWLRhjkLYKiTOf0d-n-1922raX.png) 
        - We then match Sells(x,G) with Sells(JS, G), binding x to JS. Then we add a Go(JS) and make sure that happens after start:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Noe6oziLxTFsb5idhsw_hKKaNdHNwV8t6qHVc52jg6WNu7I4u3lRT85p2ECOU8C9kdbPTJ4GfCZl8lRP78mANWh7JFCREu5dsINnNFgCnTol0jWPPETs7z4ewwISwUO1.png) 
        - What's the problem with the following and how do we solve it?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/MfVXhrCRmkRGfar8m2gqzjMq-gS3tgetaDXjFTA8V2Wl_gzJ32oVHkxFONrsWAyIeSQ2ZFzbcu9zjIwWIRV1mzMNUS_JFko4FMuQBF34ww-Vvbr12jtpN8uylnPSAdoV.png)―We risk invalidating the Go(JS) if we Go(HS) as the binding of At would no longer be Home. 
E.g. Go(HS) **threatens **to **clobber **Go(JS).
The planner can try and solve this by introducing an ordering constraint: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Tl-Wy5V3OkEvyY4RfQQuHH8uyWySjPPvBN8JRfYydf8ZOdykZKlctswYYNNZWSxlxoIPioRThujkS9EH5WQ3Z5iAibzv-nZscaVFVF78Ggs5Kb7evOo5HI1XVW4Dc0dK.png)
E.g. we add a causal link from one to the other and add a precondition. 
    - General algorithm 
        - Describe the general algorithm for forming a partial-order plan (without variables but with a partially completed plan)  ↓ 
            - Select precondition $p$ that has not been achieved, but is associated with a plan $B$.  
            - At each stage the partially completed plan is expanded into a new collection of plans. 
            - Either use an action to get p, or create a new action ($A$) to get p. 
            - Then add Start < A, A < Finish, A < B and $A \xrightarrow{p} B$.  
            - If the resulting plan is inconsistent, generate all the possible ways of removing inconsistencies using promotion or demotion and keep any consistent plans. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bSKPU9JOS01HSIxsVjTxtVbP8k1LEeaToWHr-l-PNEwJA5kxHRwW_DqhcyL6V_zDjautCPPQdCZIsBZUBRAdavvtAPuvHdP2YePu-A34RtDiKPXZo0Mk8mLqJ0cfUw0u.png) 
        - What is a possible threat, and how do we deal with it? ↓ 
            - A possible threat is when an action would cause an inconsistency, **if **the variable associated with that action was instantiated a certain way.
E.g. $\lnot \text{At}(x)$ might pose a problem for $\text{At(JS)}$ 
            - We can handle threats by adding an inequality constraining, e.g. $x \ne \text{JS}$. If we would introduce a conflict, then we discard the partially completed plan as inconsistent.
    - 
- **Lecture 10 **(Planning Algorithms 2)
    - Using heuristics as planning 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NBrHInkHb7-xkPRTPF5DDkVdm_o04Tt2dFsQgyWa4eaXiL7z6N96bGv0Y1MlwFlGEWouYUSWJOAj8hCIr98teHsISmJEInB2hbNu8ZAiIGVKerajLWf90CdOoeY46S1G.png) 
        - It's a lot harder to measure distance to goal, we don't know how much more work a plan needs. No representation of state to use.
        - One heuristic would be, choose the precondition with the smallest number of ways to satisfy it.
    - Planning graphs 
        - Planning graphs apply when it's possible to work entirely using propositional representation of plans.  STRIPS can always be propositionalised.
        - Describe the process of building a planning graph  ↓ 
            - First convert your predicate (action) to a proposition - by instantiating all the variables all the ways you can think of:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CSYpGSX1qZwN5Kl6IwkyHY7bWwAERQlXJ_UXTKtmpQgpnAMjNK5JRzvcrL0jYFtkMAwtXvShFsbUZwqEUT4EIM8UAXtQHdcAKZ5DpMOJRpcY9Ch5XtHmR2dgtvTZAxEf.png) 
            - We then first describe all the state we could have to start with, e.g. $\lnot\text{Have(G)}$, $\lnot\text{Inflate(G)}$. Then enumerate all the possible actions we could take, including the action of doing nothing.
Continue doing this until we get the combination we'd like.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6tHJLNrOMEQLilkHmrFzyBYfkljFNNjZ6QvQ7864WmJL1QlavzfQNLAK5IPHSofpMGST_oOKobbDqGJXsLinOuWLIe9gFk3Osj8_A6CdwIR_tSg6KeVCTM6SRHRQSxHd.png) 
    - Mutex links 
        - What are mutex links and what are the three types of mutex links for actions and the two types for states?  ↓ 
            - Mutex links describe which actions and propositions couldn't occur together. 
            - Type 1: The actions negate the effects of each other: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ju-Z9cSHnCeHby-VMUYvM-mdQpC24ZwC23kN1VNRccDva_wrBYGzvxX8Eo6KRX9WCphLBdrq2IHwDmGTgOQrZQow8TyfZ1T32zAFRg6gzXFYilDTB1BIguaDucF91uAG.png) 
            - Type 2: The actions interfere - e.g. the effect of one negates the precondition of another.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GKh23seyQT7fjzSE5o5JvJDiwval2I6WXSowHQa7dt9UhMvNHZQJa9My1pdi4ds_PITv9BJoII_PWF83sWYmBGfyBL1CkgzoBYymEi_udbgmpHBaxrlptFyErkUqFASs.png) 
            - Type 3: The precondition for one is mutually exclusive for the precondition for another.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/siws7YUqcQsr-ZzKETCdOvYyhpdHktcXKgzOAC_7MZWElbhiUme9X3DVQQfNWrHmlTD_rjJdF072nvZWETXFFlBRS98hpQfOjuNrrnNgyuU10XXL4ygVPZ_nu9P7oZUa.png) 
            - State Type 1: We mark a pair of propositions that cannot both be true simultaneously e.g.:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/OGgaVa0qZReCNr2nq3LFzQRPbvofTF1kGz-xMj2iiCkWiTywAYXObxblv2Io3If4X0fXmw_C_yGtIrcSEje4VsElCOWmTCUPKFUrZwSYWAv4LC_sU5HnPjvOwsWP1PJ0.png) 
            - State Type 2: We mark a pair of propositions that were created by two mutually exclusive actions.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1xVBG3PVdlvBwqvYogrbM12JFVvqxs0hCC9U94f6xz_wDjn9mgeSXEWUowCd3PcLbEybSpDIxRLAK1A0NE8n8jcUTbT-fRLYyv7_OC55vj3JfXUzAfYpvEx5C4BrMl58.png) 
        - When do you stop building a planning graph?―When two levels are the same.
        - What do you know when you reach the end of a planning graph ↓ 
            - Anything not on there **cannot be reached.** 
            - The level cost of a proposition is the number of the level it first appears in. However, this could be an underestimate as you can have multiple action usages at each level. **It is an admissible heuristic.** 
    - Obtaining heuristics from a planning graph 
        - Describe the features of max-level, level-sum and set-level heuristics ↓ 
            - Max-level: Use the maximum level a proposition occurs at. Admissible, but can inaccurate. 
            - Level-sum: Use the sum of the levels a proposition occurs at. Can overestimate but not admissible, useful if goals decomposable
            - Set-level: Use the level where all propositions appear and there are no mutex. Can be accurate if goals tend not to be decomposable. NOT admissible.
    - Other points on Planning graphs 
        - What two things does a planning graph guarantee?  Explain the confusing one. ↓ 
            - A proposition that occurs in the graph **may **be achievable. This is true because we only look at pairs of items for mutexes. 
We could look for more, but the computation cost outweighs the gains.
            - A proposition that **doesn't **occur in the graph **cannot **be achievable. 
    - Graphplan 
        - Graphplan extracts a plan from the planning graph.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QCR1YCiSmsh8lcJScHBAef8U_2kteo0WO5Wj_aFkUwCab5sfE7pORsd7gYXSAbSRbvq8G-X5tsnUb5Fme04Qr53fSFQ7nmQRCcj8HeNQnMHwDjVgGuBGZb39u4ArwkGi.png) 
        - Explain how you extract a plan using the Graphplan algorithm  ↓ 
            - We start at our final state in the planning graph and take the desired state as our start state.
            - We then note that in a search problem, reversing actions will result in new state.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9pp7xdYyhYpMBLQJMeRWE6uLyOKNtgYszZl5M17fEaMbiebmN68X1e_dg1Y80Yr-z-MXhwjlXGU-1VU9moVJ2K4Up57A1qIcFj4P79x91v0PqszpyG-yAEJETNwaGp3s.png) 
            - So we choose actions that will result in new state, move to that new state and repeat.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pqXgOnMc0gjdZSytSkd7Wyt_uKKYhcwx-ehIRasKlVidjl5aJjpYG_PUW8UiqQXifSUbrZd-qPQd1FUtMCt07q_dYgfmozuRKZosgM8xWVvQJixWVlyIIw7f13nDWVGu.png) 
    - Planning using propositional logic 
        - Give the basic idea for using satisfiability testing for planning―Make a sentence of the form: ```java
Start State AND
	Description of possible Actions AND
	Description of Goal
```Then find a model of this sentence, e.g. instantiations of variables that make this sentence true. 
The possible actions will vary with time, so we iterate over the times and generate the possible actions up to that time. Then we find a model.
        - Start state:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZqKJDwTiDnCx0GEBKzn-mT3sfNnJAf0bBX3lGqONWOpFn7jgGRkXOJnOrMBCiAD8_qH_Mooc1N0tFA6ON3f43nhsYhB4wxvS6NZ7dxK4gUOKC-IwMdl6o9L0x9LeRAqW.png) 
        - Goal and actions:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U_Qu47WmAIv_hDP8p0SESJsFVls9NrnNwV7ZheHGk_W5yYIZFXeCPL0Cs62Aa-_W5tXbMxLG-59XERo0pXGACKM41ED5EiSbTAHV1XJEWIbxuWiI3AdGBv0H2-PNeiy3.png) 
        - We need actions to encode that each person cannot be in two places at once: So we need precondition axioms
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4QOcjcvEiv87_yxhZhGhEw5w00XeyQ0szmPNof9OcqV-liVBFobAX1qgDT1I9e65Kt4SneC-kRMIzxt9iDqq2ggsVgF3UpChfVsmIeoYlNB-70fXt_DBtbZiZ-riHoOO.png) 
        - If we have three places and want to ensure a person isn't at two places at once, what's the problem with simply doing:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bK0m6bN4f8Q43ii9pesf5d_ZLpimwnpW-LaExELOxFWw2neISIIDcFI78z5bJhuN_E4CfM_I673EeLNDO1cZYyd-6WV1QjGe5v26-Jz4mIF8TYoFh167CP16xsnUAorr.png)
?―This will generally result in totally ordered plans, things always occur in some exact order. 
    - The state-variable representation 
        - Another way of representing planning problems, which is easier to convert into a constraint satisfaction problem.
        - Domains in the state-variable representation are methods of {{organizing objects}}, e.g. $\mathfrak{D}_1 = \text{\{ climber1, climber2 \}}$.
Relations and functions have arguments chosen from {{unions}} of these domains. 
        - What do functions (state-variables) input and output in the state-variable representation?―The take a current state, and a domain - and output a subset of the domain. E.g.
$$at(x_1, s) : \mathfrak{D}^{at}_1 \times S \rightarrow \mathfrak{D}^{at}$$
E.g. we ask where the Gorilla is 'at' given a state of the world, and the function returns that the gorilla is at the Jokeshop. 
        - What are **rigid ****relations**?―Relations that don't change over time. $\text{sells(jokeShop, Gorilla)}$ will never change! 
        - This solves the issue we were having in SAT. We don't have to encode that an object can only be in one place at a time - our function will always return 1 place!
        - Actions have a name, a set of preconditions and a set of effects.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1wOanK-zs0IB-5mPWOudZeqS1zdxoLZQBWJmV2tt1gpH0reWaBXEWnh47XlYOqlz8Sw5OQBZkakeqAALnEJkAj_sWkFtJaHxKRjPxpnHaRfqy3xVihCdsN80WjzLsAsj.png) 
        - Goals are sets of expressions involving state variables, which we want to fulfil:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4bLtIRlVvU5EzATiOA3-fjaVaI5-XpVPMWxQ3loZuDBgVPj42z1XbVyv5Cn1ROA5ZhBGBadEVOQi8-UU1i3ea99X4fyGYM0nlrmPGCdI8YHzsCqJ_Sbf7R5_FaN0fxW9.png) 
        - What is the **state **in state-variable representation?―It's just a statement of what values the state variables take at a given time. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/umuDMYCowPbMAxh6ZwHVD19c57mo_2Spu_XdM8y7E5vvGN9k8mXQ6Xlg62Vg6dr3Qig4KYYrGFNgQ4bGeQcRsQtrnwa1u2drYvOE2t0GGxe6QDP7GDi2Oq5f7Q_NK6FL.png)
Exhaustive enumeration of all the functions with all their possible inputs. 
        - When we apply an action, we first check if all the {{rigid conditions}} match - then we check {{preconditions}} against the state. Finally, we {{update the state}}. Note that actions only update the state they effect, solving the frame problem (kind of).
    - Converting to a CSP 
        - **Step 1. **
Encode actions as CSP variables. We do this by―Encoding all the possible values of the function in the domain of the variable. E.g. {sells(jokeShop, climber), sells(jokeShop, Gorilla) } etc.
Additionally, an action can be none.
        - **Step 2**  
Encode ground state variables as CSP variables, and a complete copy of all state variables for each time step. How do we do this?―We have a CSP variable for each state-variable at each time t, who's domain is all the possible values it could take:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n_yWZ8H3rO3wxl8DLT9c_8XKDwxMiDW4LPrtne6mjZewrfGedJl8rhhROquF9Ohys4eCKGh4YSswyoEcdhyJfng_UxLu_BSNvdQeMNuhhwsVmUD2ec_dfJQUFL7Vq3nF.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2s7mTsWTqdcIHIcjNMkNAWc44LmESqlwWZCAE0YFqU03Wg8jeD2hiHIDqEBRf62qytVP6aJQIUABsTO57SaXZKrGkI9EB9kC5-i7PTAo4FV9xfvYf44GkoV9F6aB6vb6.png) 
        - **Step 3
**Encode preconditions for actions in the planning problems as constraints in the CSP problem. How do we do this?―For each time step t, and each ground action t - encode preconditions for that argument using constraint pairs. E.g. for:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/vEqavql9HhJZvF87dntE61NCmpdoFag9xtuYpD6jz5XTis5UyCGtgabFkLO9YJeNK3NA2HOZrPJ9vTbPI6MQ5sFVEZ-cGU5MGCConDZW5vnJTlZmBRmnp989dKLfxJIJ.png)
We'd have:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ZZywqS3mAE09nl9sUv-7y931ITkkn33Kh1vsCK6mwALkk7awV9Z697s3eD2H0ZffIQagAbFmf7ZoSMFrrHmkSiy57aLIdnJO-xsaQlW43jHrjrivDwmDtRV0M_OLcary.png) 
        - **Step 4**
Encode the effects of actions as constraints in the CSP. How do we do this?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0TWra-F9CuksoTIyXC-9F9O6Mt2o77-_X7JFuauBqx5hm-hP9RYG-eFWsBzptIELoTYliwYR6XH3FdJXHp-0vqRkID1MwNMz2GVHxSjZbxU6tvhUARh2BJkroGhg-oWb.png) 
        - **Step 5**
Encode the frame axioms as constraints in the CSP
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_4GYupIADjdBENJO8fdo765TWfVhl_Kf2j1OyK8wvIRx0AoHI6gCRuVzYKAHNyk7ZSOJee9VstCYFElXPuJHCbYobcWBVHxpEBqSnkqZQlAuh8CB0jMsn7fkr7SE-Ed5.png)

        - 
- **Lecture 11 **(Machine learning using NN)
    - Supervised learning with NNs 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NFxRwqGXC1u1nDsywfVj_VV1t3GYQ1O_UII6k23iumGubA-mP9DNYSsrSZnBqacKnlOVpfgGWLMZy29PQoZYvo_lob_YtIwbBdavhSgLWcLBiPF6T8n2fMahvMdzYwr5.png) 
        - Each collection of measurements can be written as a vector:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/C2rsFKJyDjTpWrJcVDczqGEbqBKDqhHVhz1p1C2KlXay4J8x6EP1vylytu4jb7t2z-C5eET2fY3KQayZI_L4F1tz9D1F_DYtpsuL7Iv5c8Zi0tLcZIOL4pj2yH0ySlMZ.png) 
        - A vector of this kind is called a feature vector, where the measurements are attributes or features.
        - Features will be:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cpHLnPQ_zAzyAQ3vXQZGFC_Fm4pO02NRS_meIsH9mWQqmbGj2MG4tikpI4zjTfsK9yt0tA4nnLKU801VBv3qa_nkdjelK3wn-2CIg7WKSdHcrXfIa0jvD_BBYhl4DqZv.png) 
        - We then combine the features, with a dataset of patient histories and whether they had the disease D. Forming a training sequence:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1bHSDnc-VD6Ohu0YgAj5EvfT06DpQwEXH2AkxZ5TwfGItM0yMgpsNkT8eheKfyZn1vWZeqTT7jT8-QN59JJt1FuRjwTgpUGXWTikJQKYnZZnNoo2wEWAPfHaE9RPhw-H.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yTr9utsAxe_z0gQ2e6w7RV0PAoSJipaR5twHTdNHt6TDDZOO0K8N6RJJ_mC2izX1ctYh-KYBVPmnoUO73Uc5Jv0fus2Lee1c_V6k2HsrsiZvPfTqt1bXNF27zWk2H5fW.png) 
        - So our hypothesis can be viewed as a function, takes a feature vector as input and outputs a hypothesis
    - Classification and regression 
        - Describe classification―We assign the feature vector to one of c classes  ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3h7hEeekIN3SDfZThk8tLwfSqG4sA7z9ezINUNCoS_0qfVy7z2I9ZZU2XdU3xHpTONOK-faqwmMqh_q8wcwfUehPynHO0KbF0BHDZwBPIAPwo2njU7N_gAdUF9al-vHG.png)
These will contain, has the disease, doesn't have it AND importantly - The model doesn't know! 
They might also output a certainty - if uncertain then pass to human.
        - Describe regression―We assign a real number to our feature vector - we can then assign this to the closest class, or it could represent a physical quantity: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6tHD8rrx7-XhmJkPt_DAJ0Qiz-5h-9cm14fRzIlkJViaGi_llOgNhY0AjuZFFQJsxQ6AE5-g65NPFv4MtewA0oDQ8tqpHlAcmpa0xEeR01g1z9IoxHHakTm9S1nZdtPl.png) 
        - We don't want to design h explicitly
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LU4CromGKMgkvCyndauVTlb5XHIW6lSjMDPSFLebnutONmnAgIkArpM-2sPJVCYXKWctLwHVnxfHAutXb2VJ3ySkZR_9eVugP8EIKISV84t5G7OTbb4CK7IDLS8COm8k.png) 
        - There is generally a set of hypothesis **from which the learner can choose**. We call this the hypothesis space:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-eGAsW7qpd9fl1XGcxwn8FEvljsniM8q4NpnKg0DCEppxivkvPsi3Y1lxsyDQ2AnLWWX7ufPbIAqlOFexCamxzo-AiIX5nW2RDl_CwO9nxEIV0l-cdUySeGuUyUF73-w.png) 
    - Supervised learning = Curve fitting
        - Nature picks a function from the hypothesis case, we don't know what that function is and we only see points on that function (training set with noise added).
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nOb2l9ZSOpQ2VHVBNNZNNnQcVlLCCv5qpYautX0Cggl8_PpNLijmOfWUYgOEa11-Gl4jJnlWeRDH1GhF3Bvubj-h8dR8dpWrP32pCr6NZwIjJ4qcpJLggEwy0wSHTBgh.png) 
        - We want to infer h, based on s.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/d7ZsQ6x6ZuXOHC1dMz8btuzkJ35gJ4p1vj3Kk7YO5hnqMD0x-kwCyeS8YdTdbH2g1UW8J8JuW8Pf2JqLZF-AwmXksr-KibtTXC_xZ_SqT0ctophB05pH9H_X-RvWv0YA.png) 
        - Describe how we use the following function to choose a hypothesis:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mNflJQJtCPKAjHamBslxgs5df9AlyjibPLa3IqFajRgHUIAqYadvhRKGflauimpg68yJkeNNeoOyqAJLHDbKyfjB8-UINsX_8USQlHVsLyBsJDRSGy_8e4bo4hQf_Ce2.png)―We pick a h in the hypothesis space, that minimizes the mean squared error of the entire dataset.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VVS9ASsfaDAUCrLvzpx3XUD90MhV47dwCZeVVHDWLuwtWBvKT3Qc5lCjr8w7QjnQG_l-cudpzfO2cfGU-cPQAuqV-IvHkBSBNa5DidgChQRbYaTnt7npZMio-Z9LBAr2.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KIKez7RuO4sWWjrR1Mu2re5pWqoP4mhe4_6YkIL0JQcN92JLzWsPFnNtkCnmm__Tn1MWCYpLbYxj0d6ohKOPgGcEOuk5s3PrSgta_lH9lsXV7upmUcZV9Lq5Ad_e1ZyA.png) 
        - Problem: What hypothesis space do we use to choose h' from? If we choose a polynomial of a higher degree we might be okay, as long as we don't lose generalization (overfit). (We try and learn the noise)
    - The perceptron
        - In practise we'll have more than a single dimension, we'll want to do curve fitting in n-dimensional space.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uiTv0x6gipmpj5WdXyHLDWVVuOdp9Zh3cjN5tw4cLT3VEaGOsVlbbcG03yhH7Y99jEWWHCfV7f6TA9It1ymUzF8FfwJmFnO83j84uSNQhHfwm7O7MQeXyHJLDWjV6aEg.png) 
        - Describe a perceptron―A linear function modified by an activation function $\sigma$. Where the linear function is the sum of some weights and inputs and $\sigma$ is usually a step function. 
Now we use ReLU
    - Activation functions 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iXokJ8FMcsBF-W4WyRLh1-Jf70uRDq2cpNe7ha2R3K-MeeCeY0bEKnxZtPyQswks9UIccTfFRy0-GglgaQ5BbDaMKsyYru8egwhTGDf3m8zg34Gsec0I86fAJg0ShMWw.png) 
        - What is a Linear activation function forming geometrically? $$\sigma(z) = z$$―We form a line, plane, or hyperplane depending on the number of dimensions.
    - Sigmoid function 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8IWssj-aMg8ePxxDw9kXIcQxU5vN2SRGfv2KqwvFDb2BpcvKj3Hiax0z563FidA2ypfapNeYo12Wm43zy1IueVg8ZVkHBPSEVQ7MwT5IunL0Q9abN8yS_0y1KXd8aMk3.png) 
        - Give a reason to use sigmoid over step function―Sigmoid is differentiable, step ain't.
    - Gradient Descent 
        - Assume we're dealing with a regression function and $\sigma(z) = z$. Our error function is the mean squared error.  
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lJXOTkvBmJjbXYTlbV3USLxQNCYfKmqk6acosfRxP-psfVddlWr6Z2CH9R0XJ2hUhxrgDLMA6gtKt4JRmDE4NIxRsfyz_9Lcjn6Y_RruCPhprl_xXo6vwuk3qWgF2vsN.png)
We want to minimize this error, how do we do this?―We perform gradient descent with a set of weights. We compute: $$w_{t+1} = w_t - \eta \ \frac{\partial E(w)}{\partial w} \bigg | _ {w=w_t}$$
Where  
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u5-P4H92v-qoq4W8_cOpI4FnbM2lK_Nfy-ENdLm54XmgwZ40CCRlC_XLRRMD1lded148U-4eXC9e9-xEUWMwj9czdfP0Mr68ETI0MjSLPuaKEPoRYxHTXq0kQxIbZxhY.png) 
        - Explain each step in this derivation: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5fRbe9IwVZwAfaBJ9r5RYDWFnAQun0TKxJmfyhCOrUB91VUCQDQb-Ic4aMPz3gWgbpUzSesDSR_JiIXk4PIp51QhxkBAqRmEhKFscS8bcan55KC9h6Uxn67D94IE-8CO.png)
(ignore the blue arrow)  ↓ 
            - From line 1 to line 2 is straight forward - as we can always swap derivative symbols and sums. 
            - From line 2 to line 1, we apply the normal chain rule. $\frac{d}{dx} (f(x)^2) = 2 ( f(x)) * \frac{df(x)}{dx}$ 
            - Finally we note that the j'th $w$ will differentiate to 1, leaving all other w's as zero - meaning only $x^{(j)}$ remains (remember x is a row vector so the j goes above).
        - What is the same for each weight and what varies in this (the derivative of the error w.r.t the weights): ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yhmelvT74db_ETT6NQftEseQMk2-9jdpfwZ-G4AxOUsFt5jB2S42rzjdO2A89ujixk4K2OJh8cypyNFkGfiB0AtrWa6Hv0M155qxaf0K89UIE9BVZDEr5lR7E4FOF6Fl.png)―Only $x_i^{(j)}$ changes - everything else stays the same. We thus gets:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V799jHKj7iaU_ObjFRJ6bsxd95NYF6CigOixlf_QW6wRXeDo28vsn9e8_p9UkTSeqUk_3DxUVe2FRYG95ioxU8XgYuKyck4DF0vrvxLlZ1ORpyhKAjnNh86RXcpN4-k1.png) 
        - E(W) is parabolic and thus has a unique global minimum and no local minima, so this works well.
- **Lecture 12 **(Deriving Back prop)
    - The parity problem 
        - There are many problems a perceptron cannot solve:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/J3r0UK724BtLVsALCgD45be3r5EbjA4T_VJ9KlY6bAv21sgLP-t7Nzycx1QzBaJ1k6YqCvT-TDO_2RzvhcNGdnfxj-daFMtPRMu6uc05h5Lp1Y3Q-AoBtN8cOzAIFXqr.png)
We cannot divide these! 
        - To solve this, we make each node in the network a perceptron: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FVtPngQUatZvYzTOaPbitWVDHaSwsKs-Mdm_zynGNeu2QVamRN1Osrhn60bkXvAppawd86ZhSr6dtPSGRFqHhOEJyB_FDDwx0VipN2bUvlOAdjpDLkCjC5KT2iUeWEbX.png) 
        - Directed acyclic graph or perceptrons forms The multilayer perceptron!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8aS4Bh1x9u-Enhtb1VQ8So3BDj_vyOZgujQycUGdRtMnUDX0NnnVG2MA1E5PXX6lZ3EExxeGdlE_OPOhC4PmRrpTCC6ailquu1YMZnoj3UjERVFNteTcMqY1gSDwCobJ.png) 
    - Backpropagation derivation 
        - We want $\frac{\partial E(w)}{\partial w}$ which we calculate using $\frac{\partial E(w)}{\partial w_{i\rightarrow j}}$. E.g. for all the weights going into our output.
        - We can break down our E(w) into a sum of many E(w)'s and then sum that, meaning we can find: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Aa6kLp4wrr4GVSy_L_ShqhGfscb6qvtn5ERHV-24nw3i-TIOwYh-8SmTkq1blDDYI4UzogpI6jtVTGATjECEPCjsCEjb5f66-u23aJMTi1jOr-N-pCn-0jDqXNHUrkff.png) 
        - We start by saying ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FXF5prL6Yp0W21tcbmaPhtEHi1uuqDqqMYxdb_9xV-HZdosA8iDzV3eYkqLc4rRgmccyECCpHDAT1v3hFGEom4H2ZqWCFYRJJvv9jJeA90zFJwh-OMZOhbf3R3jNyxiy.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_WowIbcgamAWTRkkIknDHyjoj1cJQ7VmNXVcKSCC5PJ6ia9TcSUPTjyNcvz6rfwP0BLhElb9eGSJUqNeUGGLmpMPX9AlIOFcgjsOOlC8M5dGwRcSn8GvJwg3uJFEsFmZ.png). What is $a_j$ and why can we do this?―$a_j$ is the "activation", more straightforwardly it is the weighted result of all of node j's inputs.
Clearly the error relies on how we change the output of our node, and clearly the output of our node relies on it's input weights.
Note that $$\frac{\partial a_j}{\partial w_{i \rightarrow j}} = z_i$$ 
        - So if we combine these, we get:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Co4rqkkeEKhUskptVQ_SyFlGJXbJXyd083uUsoRS6vrgmPecOdvG1jKO1blEb8Pp0Zm4pxyHD5VI2VLoLo7U214wYhkvba4qQUuXq8-reH0bZT0ya0T2rW62CCmn4jn2.png) 
        - So we want to find the value of $\delta_j$ **when j is the output node! **That is the node producing output: $y = h(\bold w ;\bold x_p)$ of the network. We then find:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eOVk8B9IDB_hZo3cBdzFuzmYJu8B8uIFFcTSrwLdMJc_ltz8GlAZw4ePjjqMfoikDhxY5SmoOvD5wnFFPgawRNPAX74FWk3zcuWreD0zsnTRx8FQHsz1O02ixasmXpeO.png) 
        - We can easily find $\frac{\partial E_p(w)}{\partial y}$ - because the error is defined in terms of the output node:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/n3qKnS-T6LCEWyc79L-F49Nsf8KsgIX6cI0f3FUqlxs7scs77hz1-8XE3cnlD0peWFkJ_7WLobgmyvsjvNUmhae3oC3iEb_-I3FepvNc7_DId9OCU9-396KHQrGMC8JB.png)  
        - So we work backwards computing deltas, we assume **we know the deltas for all nodes further in the network.** 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tOj5-_bijxt9Qcg-duK3Fs2iteQimMcUxBPcZQqyzQKBiE3_vI1zKWCQQNfVO8XlsI2x4NRTZqN1GppKJlMrof59jTMKC8zxLJIpvkfzJ2NesSgfcRTF0ZxyJd3hJ9dT.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3kR4hUEVHOe2COYgcilluLOaj__2X7HlbnM9ywL6ukeqlMfjyqWqz-pdrLnOlGvYO_OxSmvvMX20IXc_u-S6az0IAMj3jxEB-LHEIC2HyHjyU-3Mpp8paTKiO0ywE2H8.png)Explain this derivation―We start with the total error, with a partial derivative by the output of j (before the activation function).
We then note that this is the same as the sum of all the errors due to the connected nodes, multiplied by the derivative of each connected nodes output by our output.
Then we note that the first section is simply delta_k. Which we assume we've already computed.
        - Finally we have to compute the derivative of the activation of a connected node w.r.t the activation of our node. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GDMMeOSnvENZsHKVQXPot8K9K0YCTKwMGzOG8RLLITZfTCEyGwduyxoWSQV6i9Xhy4K-AWEV5xvlLt2oKZGRB_Rj1t8qFyH2tl3KSVgsVltjVCxEhOetHZj0adkVhxab.png) 
    - Batch vs Sequential gradient descent 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/-VWPEafRfZsQPc8ndvZqWtVNHaJ7L-57iTGjDAaGAmxzzSNZV6ayZngUgG6WJvOs8sels1FKdKotaBBTzvjXOvWyaUJMGxyYJ9Bdzlvh1oTLfMFWgYT0YfqU9lHcCKEp.png) 
        - 
- 
- ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/55Eqle7fOUeSTnPmzPbkciG_m-ryibCPv6IAbY2sRBsQAnq79GQHblePjV2xWaWc0kuE_Cp9ShvVRtEiMVQeHUmP3G5hTufGlBzj6vOf6_PgMRm_LEQPgMvhn6tQaG49.png) 
- **Supervision 1**
    - 
    - 3. Search 
    - Question 1 
        1. Explain why breadth-first search is optimal if path-cost is a non-decreasing function of node-depth.  
        - In breadth-first search we examine each node in the current depth, e.g. each node in a layer of a tree. So, if we find a non-optimal path - there must be a path with a lower path cost in a lower depth or at the current depth. 
For the first case, a node can only appear once for tree search and for graph search we'll search the whole layer before deciding. Thus we'll always find the best path to a node in the current layer.
For the second case, if a path is at a lower depth - then as path-cost is assumed to be a non-decreasing function of node-depth the path-cost must be more than or equal to the current path. 
Therefore, our current path is optimal and breadth-first search under these assumptions is optimal.
    - Question 2 
        - a.)$$f_1(b,d) = \sum_{i=0}^{d} b^i = \frac{b^{d+1}-1}{b-1}$$ 
        - b.) Iterative deepening first searches all the nodes in depth 1, then all the nodes in depths 1 and 2, then 1, 2 and 3 etc. This results in:
$$f_2(b,d)=\sum_{i=0}^d f_1(b,i)$$ 
        - c.) For large b $$\sum_{i=0}^d f_1(b,i) = \sum_{i=0}^d \frac{b^{i+1}-1}{b-1} \approx \sum_{i=0}^d \frac{b^{i+1}}{b} = \sum_{i=0}^d b^i$$ 
So they are negligibly different for large b. This is because a large proportion of the nodes in a tree are in the last layer, and thus this makes the largest impact.
    - Question 3 
        - This can result in a non-optimal goal - as we aren't ordering to path cost to the goal node. There could be another node in the fringe with a lower path to that goal.
        - Additionally, we'll have to re-tread our steps to those nodes later, when we calculate the path costs to those nodes - meaning if a goal is not on a layer we'll have visited every node in that layer twice as many times as we need to.
        - Consider this tree:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gYa9GCWpSaGVHgc0Ndp9EspdIY1hQrFNT4rXqEnzjLouC2bzs7QIqM-q_NFQnb4yXEaszrFstXC8PuS2792ov9UrEdSJq-Ghkvr1aRl6snzy5GHOWY8etQ_dcIGcfTN4.png) 
Using normal A* search we'd find the goal with cost 5, using this method we'll find the goal with cost 10.
    - Question 4 
        - a.) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2pdaZZ8AKr8yTFjSCKul8KfjxQQXbgvAT50oRLBnN9jqpaZRhznu9mfwI9JvkjbDfLE94bMAkNgNdaHYSlphe7EPqCcFZMH6JG53RhI0zimxSOfy3CTPMfRRIsJBEGzf.png) 
        - b.)![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ukib90dcDeJeFydCyzlN-S63zk_dtQq12IYI2k_3B_-R5m2Pl5iqeKcWY01X0i6Env5JE7nLWP4AxFnSjbpoNA3lAccvy4nULX1sQ3sxQDjt0oOBHjPtJI3XHP4DTX75.jpeg) 
        - c.) No the converse isn't true, you could have consecutive nodes which both underestimate a heuristic but one increases. E.g.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LbRFDgmV1CJpgnoeB-fzmkkIcpeHIc_eINgI-9R7b-Dum5P_t-tK0uABGKAl4GhkjOMacH5HogudiEKgktPC-j-Ut9X_yVVBmqR0UEyVLrR6W9-icvvcEoPGHr2Kq9__.png) 
If the actual distance to the goal was 100 say, then h(s) and h(s') are both underestimates but $f(s') \lt f(s)$.
    - Question 6 
        - This might not always find the optimal path - consider a node $n$ where the two searches meet. That node might be the closest to the goal, but it could be very far from the start (which could happen if it was expanded and the edge from it to the very next consecutive node is very large.).
    - Question 7 
        - At every node, simply store the id of the next node to explore - and update that when you return to that node. Then you don't need to store any info about whether the other nodes have been searched as there is a strict ordering for DFS and you can always work out which node to search next.
    - 
    - Part IB 2013 Paper 4 Question 1
    - Part a.) 
        - Describe the basic algorithm for performing local search. Give an example of a search problem for which it is an appropriate solution, and an example of a search problem for which it is not. When would an algorithm such as A* search be preferred?  

Local search works by starting at a node on the graph, then expanding neighbours and recursively local searching the neighbouring node with the best f(s) (Usually the minimum for shortest paths). 
A problem where the optimal solution is not necessarily desired and instead a "good" solution is needed quickly are a good use of local search - e.g. NP-complete problems where they would otherwise take exponential time. For example, if we modified boolean satisfiability to instead be the maximum number of clauses we can satisfy local search could give a good solution.
Any search problem with cycles (that don't include the goal node) means local search is very unlikely to find the goal. Additionally, local search doesn't account for the total path cost - only considering the minimum path among its current neighbours (no backtracking), so best path algorithms will often result in a non-optimal solution and are thus not suitable.
A* would be preferred if we need an optimal solution, and a solution where the optimality relies on minimum path length. Additionally, A* handles the problem of getting stuck in a cycle.
    - Part b.) 
        - i.) If we reach a state where we are continually cycling between two game states (as they are both the best node of the other), **and **this is simply a local best and a global best can be found by travelling to a different node that isn't the best. In this case we could employ a technique used in stochastic hill climbing and give each node a **probability **of travelling to it proportional to the improvement in f it would provide. Thus, we'll mostly follow the best path but we can escape a local minimum if we get stuck. 
        - ii.) If the none of our nodes would lead to an improvement in our function, then we could employ restarts. I.e. when we reach a local minima where none of our neighbours improve us, we restart the local search somewhere else in the graph. We first store the best node we found so far, and when we've exceeded the total time allowance we will return the best of all the nodes we found. This would result in better coverage of the graph, and a higher likelihood of finding the optimal solution. 
    - Part c.) 
        - Constraint satisfaction problems at first glance rely only on the values of your neighbours (e.g. do the constraints conflict) but that is not the reality. The immediate reliance of a node is on it's neighbours, but it's neighbours relies on further their neighbours and so one - so the history of the path does matter making local search not well suited for this application. Local search would need a method of backtracking, as inevitably there would be conflicts, and would then need to be modified to include more than "local" state - as otherwise it will get in cycles where one node needs to be changed to change another, which would then cause a cycle and result in backtracking.
    - 
    - 2006 Paper 3 Question 3 
    - Part a.) 
        - The MiniMax algorithm uses a function f, which returns how good a given position is for a player Max - the higher the better. We then use this and note that Max will always want to follow a path that maximizes f and his opponent Min will always want to minimize it.
We start by enumerating all the possible series of moves in the game and storing them in a tree. Then we go through and mark all nodes in one Layer as Max and all nodes in the next as Min and repeat.
We continue until we reach end game states (or a cutoff) and record the value of f for each of these states. Then (working from the bottom up layer by layer) at each "Min" node we take the minimum of the values of its children and set that as our nodes value. Similarly, at any Max node we choose the max of our children and set that as our value.
E.g. the bottom left node is a Min node, thus we pick the smallest child to be our value (3) and continue.
This way the value of the root node will filter up, which will be the best possible f that Max can achieve. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sEW9XLrqtmPHOFemk9-JQR506aoujfHGPZUsfSy_qrqmD2d4J8cW70VKeLFHkruCNf7HbYFwrjCW9lK9ey5goaDFfHm0rxLLY_ObcbdlCCHenDL7r0WVohx4LSQuj3ge.png) 
    - Part b.) 
        - For a real game, we cannot explore every possible sequence of moves to reach the bottom of the tree. This would be infeasible in time and space. Thus a cutoff is required, we will apply minimax to a certain depth then apply f and work upwards from there.
        - However, this will mean we only look a few moves ahead. For a further improvement a evaluation function can be used to quickly gauge how good a position is (not necessarily with perfect accuracy), for example counting the combined piece cost in chess, using this if the evaluation function for a possible position is too high for Min or too low for Max we won't bother to explore it. The size would depend on other siblings. This evaluation function could be learnt using other AI algorithms.
    - Part c.) 
        - Alpha-beta pruning seeks to prune the search tree without affecting the outcome of the search. For a given breadth first search of the tree, we record the largest value seen by Max ($\alpha$) and the smallest value seen by Min ($\beta$). (Assume Max has the first turn, the sequence is very similar for Min): 
First Max checks if we're beyond the limit on search if so we return that limit. 
Otherwise we first initialize a value to -infinity. Then iterate through the neighbour nodes and for each node n set the value to the maximum of the current value and the result of a call to Min on n (passing $\alpha$ and $\beta$). Then if the value is greater than the largest value seen so far, return f(n) as Min will never let us get here anyway (e.g. prune the tree). Otherwise, update $\alpha$ if the value is large than $\alpha.$ 
Min's routine is similar, but we call Max's routine to find the value and we prune if the value found is less than $\beta$ as Max will never let us get here.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NNfHKTypxbeA9fm2p1gen8x5c4UvkQyuL59NNe_HeyK6kYv0vJsOa0_3pXhgpy-uLEh1E0lZlvUcxAuotaRRLaZPnr6kQXY_0jODBYgRl3R5cYX3ufitaCJttssnA3NF.png) 
- **Supervision 2**
    - [2012 Paper 4 Question 2 ](https://www.cl.cam.ac.uk/teaching/exams/pastpapers/y2012p4q2.pdf)
    - Part a.) 
    - Gaschnig's algorithm works based on a partial instantiation $I_k$ and a variable $V_{k+1}$. Whenever we attempt to instantiate a variable and there is a conflict in a variable in $I_k$, we note down the variable in $I_k$ the conflict was with. Then if $V_{k+1}$ is a dead end, we back-jump to the earliest variable in $I_k$ which conflicted with $V_{k+1}$. Note that if that variable we jump back to is an internal dead end, we resort to chronological backtracking. 
    - This is an improvement on chronological backtracking, as it only backtracks to nodes whose change could immediately impact the instantiation of $V_k$. In chronological backtracking, we can backtrack to a node with no constraint with $V_k$ and it takes longer to reach a node that can actually affect $V_k$. 
    - Part b.) 
    - When we try and assign to 6, we first try R and find that 1 conflicts with us (we note this down for later usage) - then we try G and find that 2 is conflicting with us (we note this down for later usage) and finally we try B and find there is a conflict with 3. So we look through to find the earliest variable we conflicted with, and we find that's 1. So we back-jump to 1, and when we find 1 is a leaf dead-end we go chronologically. We'd have to change 2 though as there's nothing earlier. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tnZI1PtCCQ-NGnmrvWlv94foOUHP8uP-wsvGytK0YhYg9PL6SffOk8nU80G-_xyJ3XYKwO-yCNjW1QzdrDt_ONNr9XPA_RKulF7HTVUS4SCov4ONZxdqIBr73V2YN_nw.png) 
    - Part c.) 
    - In graph based back-jumping we'd try and find the culprit of 6 - that is the earliest variable in ind(6). As RV(6) = {6}, Ind(6) = {1,2,3,4,5} $\cap$ {1,2,4} = {1,2,4}. We'd then choose the most recent variable which would be 4 and back-jump there. First set RV(4) = {4} $\cup$ {6} 
Then see what assignments we can make to 4, we find that we can set 4 to R. Then we can set 6 to G! So it doesn't backjump to the same place.
Gaschnig’s algorithm always back-jumps to the variable furthest back in our partial instantiation, this can be detrimental as the further back we go the more effect changing that variable has (butterfly effect) - when there could be a variable that solves our issue inbetween. In graph-based backjumping we jump to the earliest ancestor instead.
    - Part d.) 
    - In forward checking, whenever we make an instantiation we remove that value from the domain of any variables we have a relevant constraint with. 
So we would first check 1, 2 and then 3 as indicated here:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/N6reRgPNHvnBccavUi5gE76S-AcnWlmkP_LulnR_0iKxMwUAdIJY7tivs2JoDbC3ctaOw1AC_M5l2Fn3WvY-rZWNUyTfRLJJ5SIPMUMsMYOSdkL8tgi5GO4Qou06g1x0.png)
But then at 3 we realize 6's domain is the empty set and we need to backtrack,
we would immediately back-jump to 1 and start from there.
Forward checking detects the problem much earlier than graph-based back-jumping - however we do also do the work of altering the domains in forward checking. However overall forward checking is better if combined with a graph-based back-jumping backtracking method.
    - ^^Isn't forward checking just the method of detecting inconsistencies - the notes doesn't mention how we fix those inconsistencies when we meet them - Be good to go through^^ 
    - 
    - [2010 Paper 4 Question 1 ](https://www.cl.cam.ac.uk/teaching/exams/pastpapers/y2010p4q1.pdf) 
    - Part a.) 
    - Each variable can represent a node, it's constraints can represent links to other nodes (variables) and each variables domain is {A,B,C}. Additionally, the constraint will be satisfied if a variable is not instantiated to the same value as another variable.  
    - Part b.) 
    - When we instantiate 5 to C - we immediately notice that the domain of 3 is now empty when using forward checking. This would then  __induce backtracking__ , as we know the assignment is inconsistent - so we don't need to wait until we reach node 3 to realize that we must back track. Thus, we have  __reduced branching __ as we don't need to explore all other variables until we reach 3 and realize it's inconsistent - we can backtrack earlier.
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jgqT9TL7s4eiYvwJ-ulBJYmSyw89Ca1-r_uR4K3k4VCLbWxapNY_s3vEIdlYKe62gBX30O86ApOElmBIrA6yonEcNdaW2aQzQmAZ9QjCRDaOL3HzCKic9NemPxGna2pN.jpeg) 
    - Part c.) 
    - Arc consistency works as follows, for variables i and j in $i \rightarrow j$ - if for every node in i, there is a possible (non conflicting) assignment in j then the arc $i \rightarrow j$ is consistent. If a node in i cannot be satisfied by an assignment of j, we might as well remove that assignment from i's domain.
So we can seek to ensure arc consistency using the AC-3 algorithm, in this algorithm we start with a list of arcs to check - and if an arc $i \rightarrow j$ is inconsistent we remove the offending assignments from $i$'s domain. However, we must then add all the arc's ending in $i$ to be checked - as they may have now been made inconsistent as the removed assignment may have been the only possible one for some of them. 
However, in this case we'll simply do forward checking with constraint propagation checking the arcs to ensure no inconsistencies, when we update an arc we add the corresponding node to be checked - we'll then check all of their arcs for consistency.
We get the following:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/kaLhDpBlUxm-ox4s8K15kmpSboiTlDZddVaE9WBogJTRj4C43KEE-6JKCiMJfQZPz8yeGe3KjGb5a4rckd36gGVb6kmIwfDdEY__NkM9Zm7ODpx7hepzy5o50QqVDSrm.jpeg)
We carry on find until the assignment of 6=B. We first update the domains of our connected nodes, then add the nodes we update to the list (3 did not get updated so we don't check it).
We first check $1 \rightarrow 5$ and find that it's inconsistent and A so 1 loses C from it's domain and get's added to the list to check.
We then check $3 \rightarrow 5$ and again find it's inconsistent, but when we remove C from 3's domain we now have an empty domain and we have to backtrack.  
Thus constraint propagation finds an inconsistency faster than backtracking and forward checking!
    - 
    - [2014 Paper 4 Question 1 ](https://www.cl.cam.ac.uk/teaching/exams/pastpapers/y2014p4q1.pdf)
    - Part a.) 
        - The Situation calculus is a method of describing a problem in FOL, complete with the actions that we can take and the current state of the world. The state changes each time an action is taken, so we need a Result predicate which takes an action and a state and returns the new state.
To ensure actions have consequences we need effect axioms which describe what happens to the state when an action is taken. To ensure the world doesn't change when it shouldn't, we implement frame axioms. To check if a given action is possible we have possibility axioms. 
Once we have all of these, solving the problem is equivalent to solving our first-order system of equations.
    - Part b.) 
        - Assume $s_0$ is the starting state. 
        - $$\text{at(home, }s_0)$$ 
        - $$\lnot \text{have(chocolateMuffin, } s_0)$$ 
    - Part c.) 
        - If we are at fat Finbar's in the current state and have a goldBar, it's possible for us to buy a muffin:
        - $$\text{at(robot, FatFinbars, s)} \land \text{have(goldBar, s)} \rightarrow \text{Poss(BuyMuffin, s)}$$ 
        - If we're at the cemetery and we see flowers, then we can steal the flowers there
        - $$\text{at(robot, Cemetery, s)} \land \text{see(robot, Flowers,s)} \rightarrow \text{Poss(StealFlowers, s)}$$ 
    - Part d.) 
        - $$\text{poss(a,s)} \rightarrow ( \text{have(flowers, result(a,s))} \iff   (\text{have(flowers, s)}  \lor \text{a=StealFlowers})$$ 
        - If I have the flowers, either I had them to begin with or I've just stolen them. 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gjXfNjN2QntNjVqS5BObuF23sg-rI8GAxNOWSD61r8RThpk21vt5rnSgibAZsKGoDi8D-FuURBZRKHi10iqBcpN4hM6WcFdjzVPoH_U0iXwGPohtveFmGlX29eylLC0y.jpeg)
If we're at home in the next state, either we were there before we did our action or we travelled there. 
        - The ramification problem, is that you're actions can have many unforseen consequences. In this case, we handle the ramification that when we move to a new location everything we're carrying moves with us!
This successor state axioms handles this by also setting the location of any object the robot is holding.
    - Part e.) 
        - In FOL, two constants can be set to be the same thing in an interpretation. So to disallow the robot from getting muffins when they get flowers we have:
$$\text{muffins } \ne \text{flowers}$$ 
        - Similarly, we would like the go action to not have the same results as the jump action:
$$\text{go(l,l',s)} \ne \text{jump}$$ 
    - 
    - 
- 
