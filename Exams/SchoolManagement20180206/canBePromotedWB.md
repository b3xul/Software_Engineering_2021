# Fill table
|                                      | Coverage reached        | Number of TC needed                                                                                                                                 | Test cases      |
| ------------------------------------ | ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Node coverage                        | 100%                    | 2                                                                                                                                                   | TC1,TC4         |
| Edge coverage                        | 100%                    | 2                                                                                                                                                   | TC1,TC4         |
| Multiple Conditions coverage line 13 | 100%                    | 4                                                                                                                                                   | TC1,TC2,TC3,TC4 |
| Loop coverage row 8                  | 33% (only >1 iteration) | 3                                                                                                                                                   | TC1 (or anyone) |
| Path coverage                        | 50%                     | Theoretically 2^3*2=16 but not all are feasible since conditions are linked! Only 8 are possible (2^3, because then the path is univocally defined) | TC1,TC2,TC3,TC4 |

Test Cases:
- TC1 (0, 0, 3) TT
- TC2 (0, 0, 7) TF
- TC3 (3, 3, 3) FT
- TC4 (7, 7, 7) FF