# Quest 4

## Quest Overview
The problem today is a great example of how complex problems may only require
a simple solution.

Key language used: **Bash Shell + bc**
(for proper division, not integer division).

### Part I

For part I, the only two gears that matters are the first gear and the last gear.
The explanation with examples already show that the formula to get the answer
is `2025 * teeth_of_first_gear / teeth_of_last_gear`.

### Part II

For part II, again, only the first and last gears matters.
We are looking for the minimum number of turns on the first gear
to get at least 10000000000000 turns on the last gear.

```
turns_of_first_gear * teeth_of_first_gear / teeth_of_last_gear > 10000000000000
turns_of_first_gear > 10000000000000 * teeth_of_last_gear / teeth_of_first_gear
```

Also, since we're looking for full turns, we only want the integer of the
division product.

### Part III

For part III, the gears in between first and last gear now matter.
As middle gears are mounted so that the gears connected to the previous gear
turns as many rounds as the gear that is connected to the next gear,
this means that "the number of teeth" for every gear position changes
(instead of staying static like part I & part II).

However, if we study the problem, we'll see that
```
turns_of_gear_1 * teeth_of_gear_1 / teeth_of_gear_2L = turns_of_gear_2
turns_of_gear_2 * teeth_of_gear_2R / teeth_of_gear_3L = turns_of_gear_3
turns_of_gear_3 * teeth_of_gear_3R / teeth_of_gear_4L = turns_of_gear_4
turns_of_gear_4 * teeth_of_gear_4R / teeth_of_gear_5L = turns_of_gear_5
...
turns_of_gear_(N-1) * teeth_of_gear_(N-1)R / teeth_of_gear_N = turns_of_gear_N
```

Notice that these formulas can be chained
(`turns_of_gear_2` in formula 2 can be replaced by the left side of formula 1)
into
```
turns_of_gear_1 * teeth_of_gear_1 / teeth_of_gear_2L * teeth_of_gear_2R / teeth_of_gear_3L * ... * teeth_of_gear_4R / teeth_of_gear_5L = turns_of_gear_N
```

## How to Run?
The input files are downloaded with specific filenames that are precoded into
the shell scripts. For each part, just run the corresponding shell script:  
`bash everybody_codes_e2025_q04_px.sh`

## After-thoughts
This solution can be solved using any language that supports arithmetics --
Python, C, R -- just to name a few.
The speed with which the problem can be solved lies in how convenient is
it to code integer division vs. fractional/floating-point division, and input
parsing and manipulation.
Bash shell's `tr` is perfect for input manipulation for Part III, but then
native support only for integer division made me spend a little too much time
on this problem trying to find ways around it.
