# Control flow graph (draw by hand)

# Fill table
|                              | Coverage reached | Number of TC needed                                             | Test cases      |
| ---------------------------- | ---------------- | --------------------------------------------------------------- | --------------- |
| Node coverage                | 100%             | 3                                                               | TC1,TC2,TC3     |
| Edge coverage                | 100%             | 4                                                               | TC1,TC2,TC3,TC4 |
| Multiple Conditions coverage | -                | -                                                               | -               |
| Loop coverage row x          | 33%              | 1                                                               | TC1 (or anyone) |
| Path coverage                | 12.5%            | Theoretically 2^3*4=32 NO!! -> In practice only 4 are possible! | TC1,TC2,TC3,TC4 |

Test Cases:
- TC1 (7000;500) {wage>range[i] 1 time}
- TC2 (20000;1500) {wage>range[i] 2 times}
- TC3 (35000;3000) {wage>range[i] 3 times}
- TC4 (2000;0) {wage>range[i] 0 times}

# Suggestions

- Node coverage: Tipically 1 TC for each possible result (output) (typically possible to explore all nodes inside cycle in 1 go) 
- Edge coverage: every time there is an if without an else outside the loop, it means that there is 1 edge not covered by the node coverage!
- MC coverage:
1. If outside of a loop 2^n_conditions Test cases needed to 100% coverage
2. If inside loop, less Test cases can be enough to achieve 100%
3. Tricky: if(string!= NULL && string.equals("A")) -> we can have:
   1. "A" TT
   2. "B" TF
   3. NULL F* (first condition influences the second one! )
   N.B. In this case the coverage is 50%, not 75% because we cannot execute the second condition!
- Loop coverage: Since we can't control the number of iterations of the loop, only 2+ iterations can be covered (not 0 or 1)
- Path coverage:
1.  N.B. In this case for how the loop is structured, we can't have 8 different paths, even if there are 3 iterations and 2 branches!! This is because some paths will be impossible! Only 4 paths are possible! 1. wage< ranges[0] (fff), 2. wage>ranges[0] (tff), 3. wage>ranges[0];wage>ranges[1] (ttf), 4. wage>ranges[0],wage>ranges[1],wage>ranges[2] (ttt)
2. N.B. For how the program is structured, given the result of the loop, only 1 path will be possible!! We don't need to multiply anything! Only 4 total paths are possible!
- Typically control flow graph complicated, easy path coverage!
- In this case easy exercise, particular path coverage (needs reasoning)!
- Exercise book 2018