# Quest 9

## Quest Overview
Today's puzzle involves checking strings against each others to find similarity
character by character. It also involves three-way comparisons.

Key language used: **Bash Shell + GNU Awk**

### Part I

The first part of the puzzle involves comparing 3 DNA sequences to find a child
to the other two sequences. The rules are that each character in the child
sequence must come from either one of the parent.

Upon finding the child, we need to calculate a degree of similarity as
`number of chars same with parent 1` * `number of chars same with parent 2`.

### Part II

Part II of the puzzle builds on the solution in Part I, but increases the
complexity by requiring to analyse more than 3 sequences given in random order
to identify parent and child sequences.

I use nested loops to compare each sequence to another 2 of the other sequences
to identify parent-child relationships and print the degree of similarity for
each identified child.

At the end of the programme, I also print the sum of degree of similarity for
all identified children sequences.

### Part III

Part III of the puzzle now disregards the degree of similarity. The requirement
now is to identify parent-child relationships from the list of sequences, and
identify family trees from these relationship. The goal of the puzzle is to
identify the largest family tree from the given list of sequences.

For this, I repurposed the solution from Part II to print all families of
parents and child, then wrote code to use group all families with any of the
3 members from the first family into one big family. This process is repeated
until the family can no longer be grown. This first big family is moved to
a temporary buffer so that the loop will now use the new first family in the
remaining list of families and grow that family. This is done until all
families are moved to the temporary buffer.

Finally, the number of member for each family in the temporary buffer is
computed, and the largest number is the solution for this puzzle.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q09_px.sh`

## After-thought
I'll admin I was rushed when I first attempted the first part of today's puzzle.
Instead of comparing the characters of the sequences as substrings, I spent
time converting sequences to one-character per line,
then `paste`-ing three sequences side by side to be compared line-by-line.
This proves to be tiresome when I moved on to Part II of the puzzle, where
there's more than 3 sequences to be compared to each other to identify
parent-child relationship.  

As a problem that involves strings and substrings, I imagine a similar solution
can be easily written in Python.
