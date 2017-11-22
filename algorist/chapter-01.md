# Part 1 - Practical Algorithm Design
## Chapter 1 - Introduction to Algorithm Design

An ideal algorithm is
1. Correct
2. Effecient
3. Easy to implement - we cave on this one the most


### 1.1 Robot Tour Optimization

My ideas for shortest cycle
**Closest point**
1. Go to closest point
2. Repeat

**Factorial calculation?**
1. Calculate total distance of each permutation (order matters)
2. Use the one with shortest total distance

The book
1. Nearest-neighbor - very wrong, can hop back and forth
2. Closest-pair
3. Enumerate all possible orderings - we all knew this was too slow. ~20 points is too many, 1,000 which is a real number is absolutely undoable.

This problem is known as the travelling salesman problem. TSP

#### Take home lesson
**Algorithm** - always produces a correct result
**Heuristic** - usually do a good job, no guarantee

### 1.2 Selecting the Right Jobs
The movie scheduling problem

My ideas
1. Start with each moveie
2. Take the next with a valid starting date
3. Repeat 2

1. Take shortest
2. Take next shortest that is valid
3. Repeat 2

The book
1. Earliest job first
2. Shortest job first
3. Exhaustive scheduling - there are 2^n subsets of n things, it breaks down with large numbers like 100
4. Optimal scheduling

**Optimal scheduling**
OptimalScheduling(I)
    while(I != 0) do
        Accept the job *j* from *I* with the earliest completion date.
        Delete *j*, and any interval which intersects *j* from *I*

```python
def optimal_scheduling(intervals):
    while 
```

#### Take home lesson
Reasonable looking algorithms can easily be incorrect.

### 1.3 Reasoning about Correctness
