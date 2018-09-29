# The Ad Hoc Problems

We will terminate this chapter by discussing the first proper problem type in the ICPCs
and IOIs: The Ad Hoc problems. According to USACO [48], the Ad Hoc problems are
problems that ‘cannot be classified anywhere else’ since each problem description and its
corresponding solution are ‘unique’. Many Ad Hoc problems are easy (as shown in Section
1.3), but this does not apply to all Ad Hoc problems.

Ad Hoc problems frequently appear in programming contests. In ICPC, ≈ 1-2 problems
out of every ≈ 10 problems are Ad Hoc problems. If the Ad Hoc problem is easy, it will
usually be the first problem solved by the teams in a programming contest. However, there
were cases where solutions to the Ad Hoc problems were too complicated to implement,
causing some teams to strategically defer them to the last hour. In an ICPC regional contest
with about 60 teams, your team would rank in the lower half (rank 30-60) if you can only
solve Ad Hoc problems.

In IOI 2009 and 2010, there has been 1 easy task per competition day11, usually an (Easy)
Ad Hoc task. If you are an IOI contestant, you will definitely not win any medals for just
solving the 2 easy Ad Hoc tasks over the 2 competition days. However, the faster you can
clear these 2 easy tasks, the more time that you will have to work on the other 2 × 3 = 6
challenging tasks.

We have listed many Ad Hoc problems that we have solved in the UVa Online Judge
[47] in the several categories below. We believe that you can solve most of these problems
without using the advanced data structures or algorithms that will be discussed in the later
chapters. Many of these Ad Hoc problems are ‘simple’ but some of them maybe ‘tricky’.
Try to solve a few problems from each category before reading the next chapter.

Note: A small number of problems, although listed as part of Chapter 1, may require
knowledge from subsequent chapters, e.g. knowledge of linear data structures (arrays) in
Section 2.2, knowledge of backtracking in Section 3.2, etc. You can revisit these harder Ad
Hoc problems after you have understood the required concepts.

The categories:

- **Game (Card)** = There are lots of Ad Hoc problems involving popular games. Many are related to card
games. You will usually need to parse the input strings (see Section 6.3) as playing
cards have both suits (D/Diamond/♦, C/Club/♣, H/Heart/♥, and S/Spades/♠) and
ranks (usually: 2 < 3 < . . .< 9 < T/Ten < J/Jack < Q/Queen < K/King < A/Ace12).
It may be a good idea to map these troublesome strings to integer indices. For example,
one possible mapping is to map D2 → 0, D3 → 1, . . . , DA → 12, C2 → 13, C3 → 14,
. . . , SA → 51. Then, you can work with the integer indices instead.

- **Game (Chess)** = Chess is another popular game that sometimes appears in programming contest problems.
Some of these problems are Ad Hoc and listed in this section. Some of them are
combinatorial with tasks like counting how many ways there are to place 8-queens in
8 × 8 chess board. These are listed in Chapter 3.

- **Game (Others)**, easier and harder (or more tedious). = Other than card and chess games, many other popular games have made their way into programming contests: Tic Tac Toe, Rock-Paper-Scissors, Snakes/Ladders, BINGO, Bowling, etc. Knowing the details of these games may be helpful, but most of the game rules are given in the problem description to avoid disadvantaging contestants
who are unfamiliar with the games.

- Problems related to **Palindromes**
These are also classic problems. A palindrome is a word (or a sequence) that can
be read the same way in either direction. The most common strategy to check if a
word is palindromic is to loop from the first character to the middle one and check
if the characters match in the corresponding position from the back. For example,
‘ABCDCBA’ is a palindrome. For some harder palindrome-related problems, you
may want to check Section 6.5 for Dynamic Programming solutions.

-  Problems related to **Anagrams**
This is yet another class of classic problems. An anagram is a word (or phrase) whose
letters can be rearranged to obtain another word (or phrase). The common strategy
to check if two words are anagrams is to sort the letters of the words and compare
the results. For example, take wordA = ‘cab’, wordB = ‘bca’. After sorting, wordA
= ‘abc’ and wordB = ‘abc’ too, so they are anagrams. See Section 2.2 for various
sorting techniques.

- Interesting **Real Life** Problems, easier and harder (or more tedious)
This is one of the most interesting problem categories in the UVa Online Judge. We
believe that real life problems like these are interesting to those who are new to Computer
Science. The fact that we write programs to solve real life problems can be
an additional motivational boost. Who knows, you might stand to gain new (and
interesting) information from the problem description!

- Ad Hoc problems involving **Time**
These problems utilize time concepts such as dates, times, and calendars. These are
also real life problems. As mentioned earlier, these problems can be a little more
interesting to solve. Some of these problems will be far easier to solve if you have
mastered the Java GregorianCalendar class as it has many library functions that deal
with time.

- **"Time Waster"** problems
These are Ad Hoc problems that are written specifically to make the required solution
long and tedious. These problems, if they do appear in a programming contest, would
determine the team with the most efficient coder—someone who can implement complicated
but still accurate solutions under time constraints. Coaches should consider
adding such problems in their training programmes.

- Ad Hoc problems in **other chapters**
There are many other Ad Hoc problems which we have shifted to other chapters since
they required knowledge above basic programming skills.

Tips: After solving a number of programming problems, you begin to realize a pattern
in your solutions. Certain idioms are used frequently enough in competitive programming
implementation for shortcuts to be useful. From a C/C++ perspective,
these idioms might include: Libraries to be included (cstdio, cmath, cstring, etc),
data type shortcuts (ii, vii, vi, etc), basic I/O routines (freopen, multiple input format,
etc), loop macros (e.g. #define REP(i, a, b) for (int i = int(a); i <=
int(b); i++), etc), and a few others. A competitive programmer using C/C++ can
store these in a header file like ‘competitive.h’. With such a header, the solution to
every problem begins with a simple #include<competitive.h>. However, this tips
should not be used beyond competitive programming, especially in software industry.

Programming Exercises related to Ad Hoc problems:

- Game (Card)
1. UVa 00162 - Beggar My Neighbour (card game simulation; straightforward)
2. UVa 00462 - Bridge Hand Evaluator * (simulation; card)
3. UVa 00555 - Bridge Hands (card game)
4. UVa 10205 - Stack ’em Up (card game)
5. UVa 10315 - Poker Hands (tedious problem)
6. UVa 10646 - What is the Card? * (shuffle cards with some rule and then get certain card)
7. UVa 11225 - Tarot scores (another card game)
8. UVa 11678 - Card’s Exchange (actually just an array manipulation problem)
9. UVa 12247 - Jollo * (interesting card game; simple, but requires good logic to get all test cases correct)

- Game (Chess)
1. UVa 00255 - Correct Move (check the validity of chess moves)
2. UVa 00278 - Chess * (ad hoc, chess, closed form formula exists)
3. UVa 00696 - How Many Knights * (ad hoc, chess)
4. UVa 10196 - Check The Check (ad hoc chess game, tedious) 
5. UVa 10284 - Chessboard in FEN * (FEN = Forsyth-Edwards Notation is a standard notation for describing board positions in a chess game)
6. UVa 10849 - Move the bishop (chess)
7. UVa 11494 - Queen (ad hoc, chess)

- Game (Others), Easier
1. UVa 00340 - Master-Mind Hints (determine strong and weak matches)
2. UVa 00489 - Hangman Judge * (just do as asked)
3. UVa 00947 - Master Mind Helper (similar to UVa 340)
4. UVa 10189 - Minesweeper * (simulateMinesweeper, similar to UVa 10279)
5. UVa 10279 - Mine Sweeper (a 2D array helps, similar to UVa 10189)
6. UVa 10409 - Die Game (just simulate the die movement)
7. UVa 10530 - Guessing Game (use a 1D flag array)
8. UVa 11459 - Snakes and Ladders * (simulate it, similar to UVa 647)
9. UVa 12239 - Bingo (try all 902 pairs, see if all numbers in [0..N] are there)

-  Game (Others), Harder (more tedious)
1. UVa 00114 - Simulation Wizardry (simulation of pinball machine)
2. UVa 00141 - The Spot Game (simulation, pattern check)
3. UVa 00220 - Othello (follow the game rules, a bit tedious)
4. UVa 00227 - Puzzle (parse the input, array manipulation)
5. UVa 00232 - Crossword Answers (complex array manipulation problem)
6. UVa 00339 - SameGame Simulation (follow problem description)
7. UVa 00379 - HI-Q (follow problem description)
8. UVa 00584 - Bowling * (simulation, games, reading comprehension)
9. UVa 00647 - Chutes and Ladders (childhood board game, also see UVa 11459)
10. UVa 10363 - Tic Tac Toe (check validity of Tic Tac Toe game, tricky)
11. UVa 10443 - Rock, Scissors, Paper * (2D arrays manipulation)
12. UVa 10813 - Traditional BINGO * (follow the problem description)
13. UVa 10903 - Rock-Paper-Scissors ... (count win+losses, output win average)

- Palindrome
1. UVa 00353 - Pesky Palindromes (brute force all substring)
2. UVa 00401 - Palindromes * (simple palindrome check)
3. UVa 10018 - Reverse and Add (ad hoc, math, palindrome check)
4. UVa 10945 - Mother Bear * (palindrome)
5. UVa 11221 - Magic Square Palindrome * (we deal with a matrix)
6. UVa 11309 - Counting Chaos (palindrome check)

- Anagram
1. UVa 00148 - Anagram Checker (uses backtracking)
2. UVa 00156 - Ananagram * (easier with algorithm::sort)
3. UVa 00195 - Anagram * (easier with algorithm::next permutation)
4. UVa 00454 - Anagrams * (anagram)
5. UVa 00630 - Anagrams (II) (ad hoc, string)
6. UVa 00642 - Word Amalgamation (go through the given small dictionary for the list of possible anagrams)
7. UVa 10098 - Generating Fast, Sorted ... (very similar to UVa 195)

- Interesting Real Life Problems, Easier
1. UVa 00161 - Traffic Lights * (this is a typical situation on the road)
2. UVa 00187 - Transaction Processing (an accounting problem)
3. UVa 00362 - 18,000 Seconds Remaining (typical file download situation)
4. UVa 00637 - Booklet Printing * (application in printer driver software)
5. UVa 00857 - Quantiser (MIDI, application in computer music)
6. UVa 10082 - WERTYU (this typographical error happens to us sometimes)
7. UVa 10191 - Longest Nap (you may want to apply this to your own schedule)
8. UVa 10528 - Major Scales (music knowledge is in the problem description)
9. UVa 10554 - Calories from Fat (are you concerned with your weights?)
10. UVa 10812 - Beat the Spread * (be careful with boundary cases!)
11. UVa 11530 - SMS Typing (handphone users encounter this problem everyday)
12. UVa 11945 - Financial Management (a bit output formatting)
13. UVa 11984 - A Change in Thermal Unit (F◦ to C◦ conversion and vice versa)
14. UVa 12195 - Jingle Composing (count the number of correct measures)
15. UVa 12555 - Baby Me (one of the first question asked when a new baby is born; requires a bit of input processing)

- Interesting Real Life Problems, Harder (more tedious)
1. UVa 00139 - Telephone Tangles (calculate phone bill; string manipulation)
2. UVa 00145 - Gondwanaland Telecom (similar nature with UVa 139)
3. UVa 00333 - Recognizing Good ISBNs (note: this problem has ‘buggy’ test data with blank lines that potentially cause lots of ‘Presentation Errors’)
4. UVa 00346 - Getting Chorded (musical chord, major/minor)
5. UVa 00403 - Postscript * (emulation of printer driver, tedious)
6. UVa 00447 - Population Explosion (life simulation model)
7. UVa 00448 - OOPS (tedious ‘hexadecimal’ to ‘assembly language’ conversion)
8. UVa 00449 - Majoring in Scales (easier if you have a musical background)
9. UVa 00457 - Linear Cellular Automata (simplified ‘game of life’ simulation; similar idea with UVa 447; explore the Internet for that term)
10. UVa 00538 - Balancing Bank Accounts (the problem’s premise is quite true)
11. UVa 00608 - Counterfeit Dollar * (classical problem)
12. UVa 00706 - LC-Display (what we see in old digital display)
13. UVa 01061 - Consanguine Calculations * (LA 3736 -WorldFinals Tokyo07, consanguine = blood; this problem asks possible combinations of blood types and Rh factor; solvable by trying all eight possible blood + Rh types with the information given in the problem description)
14. UVa 10415 - Eb Alto Saxophone Player (about musical instruments)
15. UVa 10659 - Fitting Text into Slides (typical presentation programs do this)
16. UVa 11223 - O: dah, dah, dah (tedious morse code conversion)
17. UVa 11743 - Credit Check (Luhn’s algorithm to check credit card numbers; search the Internet to learn more)
18. UVa 12342 - Tax Calculator (tax computation can be tricky indeed)

- Time
1. UVa 00170 - Clock Patience (simulation, time)
2. UVa 00300 - Maya Calendar (ad hoc, time)
3. UVa 00579 - Clock Hands * (ad hoc, time)
4. UVa 00893 - Y3K * (use Java GregorianCalendar; similar to UVa 11356)
5. UVa 10070 - Leap Year or Not Leap ... (more than ordinary leap years)
6. UVa 10339 - Watching Watches (find the formula)
7. UVa 10371 - Time Zones (follow the problem description)
8. UVa 10683 - The decadary watch (simple clock system conversion)
9. UVa 11219 - How old are you? (be careful with boundary cases!)
10. UVa 11356 - Dates (very easy if you use Java GregorianCalendar)
11. UVa 11650 - Mirror Clock (some mathematics required)
12. UVa 11677 - Alarm Clock (similar idea with UVa 11650)
13. UVa 11947 - Cancer or Scorpio * (easier with Java GregorianCalendar)
14. UVa 11958 - Coming Home (be careful with ‘past midnight’)
15. UVa 12019 - Doom’s Day Algorithm (Gregorian Calendar; get DAY OF WEEK)
16. UVa 12136 - Schedule of a Married Man (LA 4202, Dhaka08, check time)
17. UVa 12148 - Electricity (easy with Gregorian Calendar; use method ‘add’ to add one day to previous date and see if it is the same as the current date)
18. UVa 12439 - February 29 (inclusion-exclusion; lots of corner cases; be careful)
19. UVa 12531 - Hours and Minutes (angles between two clock hands)

- "Time Waster" Problems
1. UVa 00144 - Student Grants (simulation)
2. UVa 00214 - Code Generation (just simulate the process; be careful with subtract (-), divide (/), and negate (@), tedious)
3. UVa 00335 - Processing MX Records (simulation)
4. UVa 00337 - Interpreting Control ... (simulation, output related)
5. UVa 00349 - Transferable Voting (II) (simulation)
6. UVa 00381 - Making the Grade (simulation)
7. UVa 00405 - Message Routing (simulation)
8. UVa 00556 - Amazing * (simulation)
9. UVa 00603 - Parking Lot (simulate the required process)
10. UVa 00830 - Shark (very hard to get AC, one minor error = WA)
11. UVa 00945 - Loading a Cargo Ship (simulate the given cargo loading process)
12. UVa 10033 - Interpreter (adhoc, simulation)
13. UVa 10134 - AutoFish (must be very careful with details)
14. UVa 10142 - Australian Voting (simulation)
15. UVa 10188 - Automated Judge Script (simulation)
16. UVa 10267 - Graphical Editor (simulation)
17. UVa 10961 - Chasing After Don Giovanni (tedious simulation)
18. UVa 11140 - Little Ali’s Little Brother (ad hoc)
19. UVa 11717 - Energy Saving Micro... (tricky simulation)
20. UVa 12060 - All Integer Average * (LA 3012, Dhaka04, output format)
21. UVa 12085 - Mobile Casanova * (LA 2189, Dhaka06, watch out for PE)
22. UVa 12608 - Garbage Collection (simulation with several corner cases)
