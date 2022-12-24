# Fill table
|                                      | Coverage reached                                           | Number of TC needed | Test cases   |
| ------------------------------------ | ---------------------------------------------------------- | ------------------- | ------------ |
| Node coverage                        | 100%                                                       | 3                   | TC1,TC2,TC3  |
| Edge coverage                        | 100%                                                       | 3                   | TC1,TC2,TC3  |
| Multiple Conditions coverage line 11 | 75%                                                        | 1                   | TC3          |
| Loop coverage line 10                | 100%                                                       | 3                   | TC1,TC2, TC3 |
| Path coverage                        | 6 with 0 children, 18 with 1 children, 324 with 2 children | 2*3*3^n_children    |              |

TC1(10, 1, 1, [3] )->1 covers 1 iteration
TC2(1500000, 0, 0, [])->0 covers 0 iterations
TC3(10, 1, 3, [19, -1, 101])->-1 covers FF, TF and FT, impossible to cover TT