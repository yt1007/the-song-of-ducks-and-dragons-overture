# Quest 1

## Quest Overview
Problem given includes a list of names, and a list of operations.

The idea is to store the names in an array/list,
and perform the left/right operations as subtraction/addition to the index.

Key language used: **GNU Awk**.

### Part I

For part I, the list is assumed to be flat, going from left to right.
Beginning with the first item in the list, move left/right the number of steps
in each given operation. When going left, do not go past the first item.
Similarly, when going right, do not go past the last item.
Give the item at the end of all operations.

GNU Awk is used to split the first line of input into a names array.
The split operation will also give the size of the array 
(count of names in the list).
Then, split the third line of input into an operations array.
Beginning 1, subtract/add the amount of steps from this position.
Before going to the next operation, check if the position is less than 1 
(GNU Awk arrays are 1-indexed) or greater than the names array size.

At the end of all operations, print the item in the names array at the derived
index.

### Part II

For part II, the list is assumed to be circular:
going past the first item will arrive at the last item,
going past the last item will arrive at the first item.

For this part, the script is only adjusted in the check after applying
subtraction/addition.
If position is less than 1, add to it the names array size.
If position is greater than the names array size, subtract from it the names
array size.
Both adjustments are done with a while loop to ensure that the index stay
within range.

### Part III

For part III, instead of continuously moving the index on circular list,
we are now required to swap the name at the position after each operation
with the first item of the list.

For this part, implemented a variable to store the first item,
and swap the names by performing `first_item = current_item` and
`current_item = original_first_item`.

At the end of all operations, print the first item in the list.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q01_px.sh`

## After-thoughts
The solution should be easily adapted for Python, since Python provides useful
functions such as split (to split input into arrays), and powerful index
splicing.
