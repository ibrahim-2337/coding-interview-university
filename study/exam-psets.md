# Exam Problem Sets: Topic Map

Analysis of the four homework problem sets (pset 1 to 4, 23 problems). The exam is expected to be similar. Problem statements are not copied here; this file only maps each problem to the skills it needs.

## Format

- Full programs, not LeetCode-style functions: read from standard input (`cin`), write to standard output (`cout`), graded by an autograder.
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
