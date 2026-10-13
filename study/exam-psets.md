# Exam Problem Sets: Topic Map

Analysis of the four homework problem sets (pset 1 to 4, 23 problems). The exam is expected to be similar. Problem statements are not copied here; this file only maps each problem to the skills it needs.

## Format

- The homework psets are full programs: read from standard input (`cin`), write to standard output (`cout`), graded by an autograder.
- The coding exam itself is LeetCode-style (write only the function), so the LeetCode equivalents below are the main practice list.
- Exact output format matters: spacing, plurals ("1 month" vs "5 months"), brackets, a trailing newline (one problem says no newline).
- Some inputs: read until end of file, whole lines with spaces, lists like `[1,2,3]`.
- Note: the PDF text extraction lost superscripts (for example "260" is probably 2^60 and "105" is 10^5). Check the originals for exact limits.

## Problems by skill

| Problem | Pset | Main skills |
|---|---|---|
| Add | 1 | `cin`/`cout` basics |
| Add, 2 | 1 | `long long` (sum of two values up to 2e9 overflows `int`) |
| Fibonacci numbers | 1 | Recursion with memoization (must be recursive and efficient) |
| Fibonacci numbers, 2 | 1 | Loop, `long long` (fib(80) exceeds `int`) |
| Perfect Numbers | 1 | Divisors up to sqrt(n), `long long`; check the limit (likely 2^60) |
| Car Value | 1 | Simulation with `double`, plural output |
| Rod Sculpture | 1 | Direction state machine, reading tokens |
| Big- or Little-Endian | 2 | Bit manipulation: reverse the 4 bytes of a 32-bit int |
| Base Conversion | 2 | String to number in base b and back, digit validation |
| No-Blink Contest | 2 | Tournament simulation by rounds (recursion or level-by-level) |
| Prime Pair | 2 | Sieve of Eratosthenes up to 20,000,000 |
| Prime Gap | 2 | Segmented sieve (values up to 2^31 - 1, range up to 1e6) |
| An Archeological Puzzle | 3 | Deque with a "reversed" flag, parsing `[1,2,3]` |
| Stack Puzzle | 3 | Backtracking (DFS) over push/pop sequences, lexicographic output |
| Job Scheduling | 3 | Interval overlap, marking a timeline array |
| Chasm Crossing | 3 | Queue simulation (two stations, capacity, travel time) |
| Parsing Brackets | 3 | Stack, positions, reading a whole line with `getline` |
| Albert's Dream | 4 | `set<string>`, lowercase, extract words, read until EOF |
| Daily Prize | 4 | `multiset` (take min and max each day), `long long` total |
| Four-Prime Numbers | 4 | Sieve that counts distinct prime factors up to 5,000,000 |
| CIMS Printer | 4 | Queue simulation with priorities |
| Lucky Draw | 4 | Stack (remove adjacent pairs with an even sum) |

## Skills ranked by how often they appear

1. Reading input correctly (every problem): `cin >>`, `getline`, read until EOF, parsing punctuation.
2. Simulation (6 problems): Car Value, Rod Sculpture, No-Blink, Job Scheduling, Chasm Crossing, CIMS Printer.
3. Stack, queue, deque (5): Brackets, Lucky Draw, Archeological Puzzle, CIMS Printer, Chasm Crossing.
4. Primes and divisors (4): Perfect Numbers, Prime Pair, Prime Gap, Four-Prime.
5. Overflow and `long long` (4): Add 2, Fibonacci 2, Perfect Numbers, Daily Prize.
6. Strings and number bases (3): Base Conversion, Albert's Dream, Archeological Puzzle.
7. Ordered containers (2): `set` (Albert's Dream), `multiset` (Daily Prize).
8. Recursion and backtracking (2): Fibonacci, Stack Puzzle.
9. Bit manipulation (1): Endian.

## Suggested practice order

1. I/O and overflow warm-up: Add, Add 2, Fibonacci, Fibonacci 2.
2. Stacks and queues: Parsing Brackets, Lucky Draw, CIMS Printer.
3. Containers and text input: Albert's Dream, Daily Prize.
4. Sieve: Prime Pair, Four-Prime Numbers.
5. Strings, bases, bits: Base Conversion, Endian.
6. Deque and parsing: Archeological Puzzle.
7. Simulation: Rod Sculpture, Car Value, Job Scheduling, Chasm Crossing, No-Blink.
8. Hardest: Stack Puzzle, Prime Gap, Perfect Numbers.

## LeetCode equivalents

Closest LeetCode problems for each pset problem. (V) = number, title and difficulty confirmed by web search; the rest are from memory and get checked when we start them.

| Pset problem | LeetCode practice | Notes |
|---|---|---|
| Add, Add 2 | 2235 Add Two Integers (E) (V) | The real lesson of Add 2 is `long long` for overflow |
| Fibonacci (recursive, efficient) | 509 Fibonacci Number (E) (V), 1137 N-th Tribonacci Number (E) (V) | Solve 509 with memoized recursion |
| Fibonacci 2 | 70 Climbing Stairs (E) (V) | Same recurrence, iterative |
| Perfect Numbers | 507 Perfect Number (E) (V) | Exact match; divisors up to sqrt(n) |
| Car Value | none close | Pure simulation; practice from the pset itself |
| Rod Sculpture | 657 Robot Return to Origin (E) (V), 1041 Robot Bounded In Circle (M) (V), 874 Walking Robot Simulation (M, difficulty not shown by search) | Direction state machine |
| Big- or Little-Endian | 190 Reverse Bits (E), 191 Number of 1 Bits (E) | Shifts and masks |
| Base Conversion | 504 Base 7 (E), 405 Convert a Number to Hexadecimal (E), 171 Excel Sheet Column Number (E), 168 Excel Sheet Column Title (E) | Both directions of base conversion |
| No-Blink Contest | 1688 Count of Matches in Tournament (E) (V) | Round-by-round tournament |
| Prime Pair | 204 Count Primes (M) | Sieve of Eratosthenes |
| Prime Gap | 2523 Closest Prime Numbers in Range (M) (V) | Same idea for the minimum gap |
| An Archeological Puzzle | 2810 Faulty Keyboard (E) (V), 641 Design Circular Deque (M) | Reverse-flag-plus-deque trick |
| Stack Puzzle | 22 Generate Parentheses (M), 946 Validate Stack Sequences (M) | Backtracking over push/pop, and checking one sequence |
| Job Scheduling | 729 My Calendar I (M) (V), 56 Merge Intervals (M) | Interval overlap |
| Chasm Crossing | none close; 2073 Time Needed to Buy Tickets (E) (V), 933 Number of Recent Calls (E) | Queue simulation practice |
| Parsing Brackets | 20 Valid Parentheses (E), 1249 Minimum Remove to Make Valid Parentheses (M) | Stack; 1249 tracks positions |
| Albert's Dream | 819 Most Common Word (E) | Extract lowercase words |
| Daily Prize | none close; 1046 Last Stone Weight (E), 703 Kth Largest Element in a Stream (E) | Heap practice; in C++ `multiset` gives min and max |
| Four-Prime Numbers | 2521 Distinct Prime Factors of Product of Array (M) (V), 204 Count Primes (M) | Sieve plus distinct prime factors |
| CIMS Printer | 2073 Time Needed to Buy Tickets (E) (V) | Queue simulation |
| Lucky Draw | 1047 Remove All Adjacent Duplicates In String (E), 1544 Make The String Great (E) | Stack removes adjacent pairs |

## LeetCode practice order for the exam

1. Warm-up: 2235, 509 (memoized), 70, 507.
2. Stacks and queues: 20, 1047, 1544, 2073, 933, 1249.
3. Bits and bases: 190, 191, 504, 405, 171, 168.
4. Primes: 204, 2523, 2521.
5. Simulation and direction: 657, 1688, 1041, 874.
6. Containers and strings: 819, 1046, 703, 2810.
7. Intervals: 56, 729.
8. Hardest: 22, 946, 641.
