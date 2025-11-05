# Quest 2

## Quest Overview
Problem given requires to perform specific addition, multiplication and division
following specific rules.

My idea is to store the x and y of individual "complex numbers" in separate
variables, and write the addition/multiplication/division accordingly.

Key language used: **Bash Shell**.

### Part I

For part I, I just need to write a for loop to repeat the procedure of
multiplying by itself, division by [10, 10] and addition by A three times.

I used cut to identify X and Y for A from input file, assuming that the input
only has 1 line.

At the end of the calculation loop, I print the complex number.

### Part II

For part II, we now need to run the operation for 10201 items (coordinates/P),
and the operations is run for 100 cycles instead of just 3. Also, the divisor
for step 2 is changed to [100, 100]

For this part, the script is only adjusted to read starting coordinate A
from input file, and the operation for loop is placed in two nested for loops
that increments y (parent) and x (child) by 10 for 101 times.

For output, the script now prints one line of output for each P,
if engraved, only the result; otherwise, the result and cycle at which the
resulting number has an x or y beyond +/- 1000000.  
To achieve this, I put a check after each cycle of operations to check if
either x and y are out of bounds, if yes, print P+R+C and break out of the
100 cycle loop, otherwise continue. After the 100 cycle loop, I check again
the current values of x and y for R (to avoid double printing),
if values are within bounds, I print P+R.

In the end, I check the number of lines with C to give answer.
The answer is number of lines containing P+R only.

### Part III

For part III, I just changed part II's script to run x & y increments of 1
instead of 10.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q02_px.sh`

## After-thoughts
The solution should be easily adapted for Python or C (might run much faster?),
the advantage of these over shell would be the ease of which the addition,
multiplication and division can be "compartmentalised" into functions that
makes code much more readable.
