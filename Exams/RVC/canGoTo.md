# BB

# criteria and predicates

| criteria                                          | equivalence class | Valid/invalid | Result |
| ------------------------------------------------- | ----------------- | ------------- | ------ |
| charge                                            | (minint, -1]      | I             | error  |
|                                                   | [0, 100]          | V             | T/F    |
|                                                   | [101, maxint)     | I             | error  |
| movingMode                                        | (minint, -1]      | I             | error  |
|                                                   | {0,1}             | V             | T/F    |
|                                                   | [2,maxint)        | I             | error  |
| distance                                          | (minint, -1]      | I             | error  |
|                                                   | [0, maxint)       | V             | T/F    |
| enoughCharge: (charge/(movingMode+1)) >= distance | true              | V             | T      |
|                                                   | false             | V             | F      |

# Boundaries

| criteria   | boundaries                      |
| ---------- | ------------------------------- |
| charge     | minint, -1 ,0, 100, 101, maxint |
| movingMode | minint, -1,0,1,2,maxint         |
| distance   | minint, -1, 0, maxint           |

# Combinations

| charge        | movingMode   | distance     | enoughCharge | V/I | Test Case                                     |
| ------------- | ------------ | ------------ | ------------ | --- | --------------------------------------------- |
| (minint, -1]  | *            | *            | *            | I   | T1(-5,0,60)->error<br>T1b(-1,0,60)->error     |
| [101, maxint) | *            | *            | *            | I   | T2(105,0,60)->error<br>T2b(101,0,60)->error   |
| *             | (minint, -1] | *            | *            | I   | T3(100,-5,60)->error<br>T3b(100,-1,60)->error |
| *             | [2,maxint)   | *            | *            | I   | T4(100,5,60)->error<br>T4b(100,2,60)->error   |
| *             | *            | (minint, -1] | *            | I   | T5(100,0,-5)->error<br>T5b(100,0,-1)->error   |
| [0, 100]      | 0            | [0, maxint)  | True         | V   | T6(100,0,60)->true<br>T6b(100,0,100)->true    |
| [0, 100]      | 0            | [0, maxint)  | False        | V   | T7(30,0,60)->false<br>T7b(30,0,31)->false     |
| [0, 100]      | 1            | [0, maxint)  | True         | V   | T8(100,1,40)->true<br>T8b(100,1,50)->true     |
| [0, 100]      | 1            | [0, maxint)  | False        | V   | T9(100,1,60)->false<br>T9b(100,1,51)->false   |