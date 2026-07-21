## Task 4

### Naive solution

The picture shows a keypad with 10 digits and 2 symbols.Goal is to calculate the
number of possible combinations, considering that a combination can be 4, 5, 6, 7 digits
long. We know that the lock model can be configured for digits key codes, so we don’t
consider the two symbols as possible elements of the combinations:
- 10 possible digits
- Number of 4 digits long passcodes: anyone of the 4 digits can be chosen with no
constraint => N₄ = 10^4
- For same reasons: N₅ = 10^5 , N₆ = 10^6 , N₇ = 10^7
- N_tot = N₄ + N₅ + N₆ + N₇ = 1111000
If we want to include the two symbols too, calculations are the same but with 12 instead
of 10: N_tot = N₄ + N₅ + N₆ + N₇ = 12^4 + 12^5 + 12^6 + 12^7 = 39087360

### Better solution

Better observing the picture allows us to notice that 1, 7, 9 and 0 buttons are very often
pressed, while all the others look brand new.
We can assume that the passcode is made of all and only these four digits.
So, we consider the combinations which include only 1, 7, 9, 0 digits, with at least one
occurrence for each of them.

- 4 digits
All the four values have to appear exactly once.
First one can be chosen among them all: 4 possible digits.
Second one only among the remaining three; third one between two; last one has only
one possibility. So, 4! possible combinations.
B₄ = 4! = 24

- 5 digits
If we have 4 marbles to put into 5 glasses (one glass can hold one marble only), we
choose the four glasses to fill (5 possible ways) and then the order of the marbles (4!).
If we apply this reasoning to our problem, we have to consider that the empty glass can
be filled with a copy of any of the marbles. By doing this we find BT₅ = 4 * 5 * 4!
We are counting twice every combination: for example, we count 01799 once considering
the first 9 coming from the empty glass, once considering the second 9 coming from the
empty glass. So, we have to divide by 2:
B₅ = 4 * 5 * 4! / 2 = 240

This kind of reasoning gets complicated moving to 6 digits codes.
Here's an alternative, easier to generalize.

All the values but one - which appears twice - appear once.
We start considering all the combinations of 5 values among our digits: 4^5
We remove all the combinations where 1 does not appear (they are 3^5) and all those
where 7, 9, 0 do not appear: it is a minus 4*3^5
Doing this we find BT₅ = 4^5 - 4*3^5 but we are removing twice all the codes containing
only two characters. For example, strings with only 0 and 1 values are removed both
when removing the codes with no 7 and when removing those with no 9. So, we add
them back: possible pairs are C₄.₂ = 6 and new BT₅ is
BT₅ = 4^5 - 4*3^5 + 6*2^5
Now, we have added twice all the codes containing one single digit (11111 for example).
We remove them and we find B₅ = 4^5 - 4*3^5 + 6*2^5 - 4 = 240

- 6 digits
Same reasoning, but with 6 digits
B₆ = 4^6 - 4*3^6 + 6*2^6 - 4 = 1560

- 7 digits
Same reasoning, but with 7 digits
B₇ = 4^7 - 4*3^7 + 6*2^7 - 4 = 8400

- Total
Summing up them, we find a total of
Bt = B₄ + B₅ + B₆ + B₇ = 8400 + 1560 + 2

