[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/IF3rQO50)
# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

For each of these implementations we divide our array into 4 parts. The 1st quarter contains elements that are too small for our pivot,
and the last quarter contains elements that are too big for our pivot. The middle quarters contain elements that are good pivots.

The leftmost element implementation:

This implementation chooses the leftmost element for the pivot of quicksort, so there are 4 scenerios in this implementation.
Either the pivot falls in the 2 bad spots of our array, or it falls in the 2 good spots, therefore the probablility of this 
implementation choosing a good pivot is 50%.

The Median-of-Three implementation:

This implementation chooses a pivot based on 3 values the leftmost, middle, and rightmost elements. Therefore there are 4 scenerios of
this implementation. All 3 pivots are good, 2 pivots are good, 1 pivot is good, and all 3 are bad.

In each of the scenerios, either a number is a good pivot or it is a bad pivot, so it is a 50% chance that a number is a good pivot.

In scenerio 1, all three pivots are good, so no matter which one is the median, this will happen:

$1/2 \cdot 1/2 \cdot 1/2$ times or 1/8 times or 12.5% of the time

In scenerio 2, 2 out of 3 elements are good pivots so there are 3 ways this occurs, the leftmost element is bad, the middle
element is bad, or the rightmost element is bad. We only care about the median, so no matter which one is the bad pivot,
we will still get a good pivot using this algorithm.

1. Here we have $1/2 \cdot 1/2$ for the probability of the last 2 elements being good and 1/2 for the probability of an element
   being bad. So our total probability becomes $1/4 \cdot 1/2$ which is 1/8
2. Similarly here we have the same scenerio $1/2 \cdot 1/2$ for the two elements being good and 1/2 for the element being bad
   which once again results in 1/8
3. Same thing for the last scenerio 1/8

Therefore, in this scenerio, the total probability is the sum of each of the smaller probabilities or 3/8 or 37.5%

In scenerio 3, 1 out of 3 elements is a good pivot, but we only care about when this element is in the middle which happens exactly
half of the time. Since there are 3 ways that we can have a good pivot here, (ex: leftmost pivot is good, middle pivot is good, and
rightmost pivot is good) we can calculate the probability as such:

We multiply by 3 for each scenerio that the pivot is good
We divide by 2 as for each of these scenerios only half of the time does this pivot end up in the middle.
And finally we multiply by 1/2 3 times for the probability of each number being choson as a good or bad pivot.
So we end up with something like:
$3 \cdot 1/2 \cdot 1/2 \cdot 1/2 \cdot 1/2$ times or 3/16 times or 18.75%

In scenerio 4, none of the pivots chosen are good pivots so we can ignore this scenerio as we will never get a good pivot value from it.

Therefore, our total probability can be obtained from adding up all the scenerios probability which equates to 68.75% chance to choose
a good pivot.

So based on this probability the median of three way of choosing a pivot is better than the leftmost element always being the pivot by
about 18.75%
