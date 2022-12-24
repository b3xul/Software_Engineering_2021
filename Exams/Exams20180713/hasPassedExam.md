# BB
# criteria and predicates

| criteria                                                                                                       | equivalence class | Valid/invalid | Result |
| -------------------------------------------------------------------------------------------------------------- | ----------------- | ------------- | ------ |
| exercise1                                                                                                      | (minint, -1]      | I             | error  |
|                                                                                                                | [0, 7]            | V             | 1/0    |
|                                                                                                                | [8, 15]           | V             | 1/0    |
|                                                                                                                | [16, maxint)      | I             | error  |
| exercise2                                                                                                      | (minint, -1]      | I             | error  |
|                                                                                                                | [0, 7]            | V             | 0      |
|                                                                                                                | [8, 15]           | V             | 1/0    |
|                                                                                                                | [16, maxint)      | I             | error  |
| lab                                                                                                            | true              | V             | 1/0    |
|                                                                                                                | false             | V             | 1/0    |
| !lab && exercise1+exercise2                                                                                    | [0, 17]           | V             | 0      |
|                                                                                                                | [18, 30]          | V             | 1      |
| passedExam: (lab && exercise2 >= 8) OR (!lab && exercise1 >= 8 && exercise2 <= 8 && exercise1+exercise2 >= 18) | true              | V             | 1      |
|                                                                                                                | false             | V             | 0      |

# Combinations

| lab   | exercise1    | exercise2    | exercise1+exercise2 | passedExam | V/I | Test Case                                                              |
| ----- | ------------ | ------------ | ------------------- | ---------- | --- | ---------------------------------------------------------------------- |
| *     | (minint, -1] | *            |                     | *          | I   |                                                                        |
| *     | [16, maxint) | *            |                     | *          | I   |                                                                        |
| *     | *            | (minint, -1] |                     | *          | I   |                                                                        |
| *     | *            | [16,maxint)  |                     | *          | I   |                                                                        |
| False | [0, 7]       | *            | *                   | False      | V   |                                                                        |
| False | *            | [0, 7]       | *                   | False      | V   |                                                                        |
| False | [8, 15]      | [8, 15]      | [0, 17]             | False      | V   | T6(9,9,false)->true<br>T6b(8,8,false)->true<br>T6c(15,15,false)->true  |
| False | "            | "            | [18, 30]            | True       | V   | T7(5,5,false)->false<br>T7b(0,0,false)->false<br>T7c(7,7,false)->false |
| True  | *            | [0, 7]       | *                   | False      | V   |                                                                        |
| True  | *            | [8, 15]      | *                   | True       | V   |                                                                        |