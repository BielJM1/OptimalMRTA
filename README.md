# OptimalMRTA
In this repository we present the source code used to produce the simulation experiments carried out in the paper "**An application of fuzzy sets to optimal task-allocation problem**".

In this code, a novel multi-robot task-allocation method, which deals with tasks with deadlines, is implemented. This MRTA draws inspiration from response-threshold methods, modeling the tasks' stimuli through fuzzy sets. Each robot decides the best task to perform solving an optimization problem, using the celebrate Bellman-Zadeh fuzzy optimization technique.

An overview of the structure of the code is presented in the following pseudocode:
```python
{INITIALIZATIONS}
createTasks(m)
createRobots(n)
t<-0

{MAIN LOOP} 
while all tasks are not completed do
    for each robot a_k do
        bestTask <- None
        bestStimulus <- 0
        for each task t_j with t_j_et > 0 do
            if sk_cl_j_t > bestStimulus then
                bestTask <- t_j
                bestStimulus <- sk_cl_j_t
            end if
        end for

        if bestTask is not None then
            if robot a_k is not located at bestTask then
                ak.goTo(bestTask)
            else
                ak.workOn(bestTask)
            endif
        else
            ak.stop()
        end if
    end for
    t <- t+1
end while

{EFECTIVENESS ASSESSMENT}
computeMetrics()
````
The code has been designed using Python 3.
