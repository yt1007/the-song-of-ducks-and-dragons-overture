# Quest 6

## Quest Overview
Today's puzzle consist of grouping `A` with `a`, `B` with `b`, and `C` with `c`;
then count the number of the upper case letter that is grouped with the lower
case letter.

Key language used: **Bash Shell**

### Part I

The first part of the puzzle focuses only on the sword fighting category
(`A` and `a`). Therefore, I broke the string into character, and declare
a variable to hold the number of `A` and a variable to hold the number of
mentors for all novices. I then read the string character
by character, if the current character is `A`, increment the `total`
variable. If the current character is `a`, current value of `total` is added
to the `total_all_novice` variable.

### Part II

The second part of the puzzle extends on the solution in part I to calculate
total of mentors for all novices for every category (`A`, `B` and `C`).
Using similar logic, I just added variable pairs for categories B and C, and
also the conditions to increment the variables. The total for each
category is summed and printed at the end of the calculation.

### Part III

The third part of the puzzle restricts the mentors possible for each novice.
Instead of all mentors who appear before a novice, suitable mentors must also
be within a given distance to the novice.

The puzzle also extends on complexity by requesting that the map be repeated,
end of list continues to the beginning of list like a circular list.

For this puzzle, I chose to implement a sliding-window-based solution. I
started first by repeating the map, then splicing the map using cut. However,
that route proves too inefficient for me to even debug.

I found out that [Bash supports extracting substrings](
https://www.geeksforgeeks.org/linux-unix/bash-scripting-substring/), _just like
Python string splicing_. I then sketched a diagram to help me visualise and
code the solution for this puzzle.

![Sliding window of substrings](everybody_codes_e2025_q06_p3.png)

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q06_px.sh`

## After-thoughts
A lot of comments on Reddit also shows that Python's string splicing is strong
in such problems. But I feel also that the optimisation of computational time
is equally important for Part III of today's puzzle. I am quite satisfied with
my final solution that is intuitive for me to debug.
