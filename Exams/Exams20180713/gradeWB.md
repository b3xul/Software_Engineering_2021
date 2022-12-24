# CFG

# Fill table
|                              | Coverage reached         | Number of TC needed                                             | Test cases      |
| ---------------------------- | ------------------------ | --------------------------------------------------------------- | --------------- |
| Node coverage                | 100%                     | 2                                                               | TC1,TC2         |
| Edge coverage                | 100%                     | 2                                                               | TC1,TC2         |
| Multiple Conditions coverage | 100%                     | 1                                                               | TC1             |
| Loop coverage row x          | 33% (only >1 iterations) | impossible                                                      | TC1 or TC2      |
| Path coverage                | 12.5%                    | Theoretically 2^3*4=32 NO!! -> In practice only 4 are possible! | TC1,TC2,TC3,TC4 |

Test Cases:
- TC1 ({{1,0,0,0},...},{{0,1,0,1,0},...}) {1 wrong: grade=-1 return 0}
- TC2 ({{1,1,0,0},...},{{0,1,0,0,0},...}) {1 right: grade=3, 1 wrong, grade=2 return 2}


# Suggestions
- Node coverage: Tipically 1 TC for each possible result (output) (typically possible to explore all nodes inside cycle in 1 go) 
- Edge coverage: every time there is an if without an else, it means that there is 1 edge not covered by the node coverage!
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