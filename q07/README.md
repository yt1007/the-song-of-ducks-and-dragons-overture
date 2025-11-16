# Quest 7

## Quest Overview
Today's puzzle involves substring analysis and appending to string.  

Key language used: **Bash Shell**

### Part I

The first part of the puzzle focuses on validating names against rules.
Notes given consists of:  
1. A list of names separated by comma on the first line.
2. An empty line on the second line.
3. From the third line till the end of the file,
   one rule per line of valid 2-letter sequences in the format of
   `[first letter] > [letter 1],[letter 2],...,[letter n]`
   where `first letter` is allowed to be followed by any letters
   in the comma separated list after the `>` symbol.

For this part, I read all names and all rules.
Then, for every name, I use a sliding window to check if every pair of letters
in the name is valid (matches any of the rules).

If every 2-character substring of a name matches the given rules,
I print the name.

### Part II

The second part of the puzzle is identical to the first part, except that
there's more than one name that can pass all rules, and we're required to
sum up the indices of names that fulfills the rules.

I repurposed the entire script from the first part, and added an index count
and an index sum to the while loop that checks every name against every rule.
The index count begins from 1 and is incremented for every name; while the
index sum begins from 0 and the current index count for every name that passes
is added to the index sum.

I print the index sum at the end of the programme.

### Part III

In the third part of the puzzle, we not only have to identify names that passes
given rules, we are also asked to lengthen each valid name using all possible
rules. We need to identify all possible names from 7 to 11 characters.

Here, the loop needs to be repurposed to also check what character we can append
to a name based on the last character and given rules.

The programme should print the number of unique names that can be created with
given rules.

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q06_px.sh`
