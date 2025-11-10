# Quest 5

## Quest Overview
For the problem today, most of the logic have been clearly narrated in the
puzzle texts.

Key language used: **Bash Shell + GNU Awk**
(GNU Awk is selected for an easier syntax in using 2D array).

### Part I

For each of the swords, the quality of a sword is derived from building a
fishbone structure from the given numbers.

I wrote this with a 2D array in mind. The first dimension holds each of
the levels (I call this "row"), while the second dimentsion holds the 
individual numbers on each level (I designed it so that it's the first,
second and third number, with the second number always holding the spine,
and the first number holds a number smaller than the spine, and the
third number holding a number larger than the spine).

In GNU Awk, an element of the array does not exist until it is assigned
a value. Hence, this is really convenient for checking if a certain number
already exists (if the spine does not exist for this row, the current number
is assigned to the spine, if a spine exist, check the left/1st number, then
the right/3rd number, then move to the next row).

After building the fishbone, the quality of the sword is printed by printing
the 2nd number on each row without space -- effectively concatenating the
numbers without any conversion.

### Part II

For part II, we're now computing the quality for multiple swords. Therefore,
the fishbone building script from Part I is repurposed to print only the quality
for each sword on each line of input.

Another bash script is then written to call the fishbone building script for
every sword.

After getting a list of qualities for all swords, we can easily sort the quality
list as numbers and get the first and last number to compute the differences.

### Part III

For part III, we not only need to sort the quality of the swords, we're now
interested in the numbers at each level, and also the sword ID to differentiate
swords with identical quality.

If two swords have the same quality, the values at each fishbone levels (from
top) is compared so that the first differing pair of values are used to
determine an order. If all levels are also identical, the larger sword ID is
stronger.

We're asked to sort the swords in descending order of their strength
(sorted by descending order of quality, value at each level, and sword ID),
and compute the checksum by totalling the sum of multiplying the position of 
a sword with its ID.

For this bit, the fishbone-building script needs to now print the quality,
value at each level, and the sword ID, so that the swords can then be sorted
based on these values. I chose to have the values printed all on one line,
separated by a colon ":", so that I can just use Bash's `sort` to sort the
swords.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q05_px.sh`

## After-thoughts
My brain keeps telling me to write an object-oriented code for this problem.
Imagine the swords as object, each having a variable to store the sword ID,
and a list to store the fishbone structure, 
each item on the list would be an array of 3 numbers representing
the number on the left of the spine, the number on the spine, and the
number on the right of the spine.

We can write methods to concatenate the numbers on the spine to become a
quality, and the numbers on each level to give the level-power.
In C++, we can also write arithmetic operator overloads to describe how one
sword is <, <=, ==, >=, or > than another sword. If we do this, we can use
any of the sort algorithms to sort a list of swords.

Also, key points for Bash programming -- `while read l; do expression; done`
loops ***do not*** read and process lines without a new-line character at the
end!!! This costed me 2 full day on Part III. The solution is to always add a
new-line character to the input texts, and then remove empty lines (or have
scripts skip empty lines).
