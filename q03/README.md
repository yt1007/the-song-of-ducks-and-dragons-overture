# Quest 2

## Quest Overview
Problem given requires sorting and determining combinations of number
series where each number is greater than the next number.

My first impression is that this is a quick one for Bash sort.

Key language used: **Bash Shell**.

### Part I

For part I, we only had to identify the largest set.

Since every crate can fit into any other crate that is only 1 size bigger,
logically, the most efficient way to fit as many crates into a set is to
just fit one crate of every available size into the same set.

For this, I sort the list of crates by size, remove duplicates, then compute
the sum.

### Part II

For part II, we now need to identify the smallest set of 20 crates that
can hold a mushroom that can fit into any crate (even crate of size 1).

As previous logic, the most efficient way is to sort the crate by size
so that we get the most efficient way of packing. Then, what we need to
do for this specific exercise is just to pick 20 of the smallest boxes
and sum the sizes up.

For this, same algorithm - sort crates by size, remove duplicates, pick
20 of the smallest size, then compute the sum.

### Part III

For part III, we need to pack all crates in as little sets as possible.
Going with the same logic, I intend to also sort the crates by size, then
sort the crates into unique sets. If a size is already in set 1, put it in set 2,
etc.

Finally, count the number of sets required.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q02_px.sh`

## After-thoughts
The solution should be easily adapted for Python, and Python's set will be our
greatest helper.
Also, for Part III, I ended up realising I overthought the solution.
Since we didn't need details such as which crate is in which set, I actually
could just check what is the most frequent crate size and how many crates of
that size was given (since each set cannot have 2 crates of the same size,
crates of same size must be in different sets. And since crates of any different
size can coexist within one set, the minimum number of sets required is the number
of crates with a size that is most frequent in all the crates).
