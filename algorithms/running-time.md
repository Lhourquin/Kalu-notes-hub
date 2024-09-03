# Measure the efficiency of an algorithm

To measure the efficiency of an algorithm, we need to know some common concepts of algorithms complexity:

Example of search algorithm in unordered list like `[9, 3, 4, 8, 2]`

* `O(n)`(Big O):
  * **Worst case**: If we search the number `2`, the worst case is to through over all elements of the list to make a comparison. That is take `n = 5` comparison, so `O(5)`.
* `Ω(1)`(Omega):
  * **Best case**: If the element we want is the first element in the list (9), we found it with just 1 comparison, so `Ω(1)`
* `Θ(n)`(Theta):
  * **Average case**: In average, we should through the middle of the list to find the element we want. That make approximatively `n/2` comparisons, but since n/2 is proportional to n, we say that the average complexity is `Θ(n)`.
