

# Black Box Unit Tests - Exercise 1

### Method acceptableToEat



**Criteria for method acceptableToEat:**
	

- Sign of carb
- Sign of protein
- Sign of fat
- Total calories
- Fat ratio



**Predicates for method acceptableToEat:**

| Criterion                               | Predicate      | (additional column added by me: result) |
| --------------------------------------- | -------------- | --------------------------------------- |
| Sign of carb                            | (-maxint, 0)   | invalid                                 |
|                                         | [0, maxint)    | valid                                   |
| Sign of protein                         | (-maxint, 0)   | invalid                                 |
|                                         | [0, maxint)    | valid                                   |
| Sign of fat                             | (-maxint, 1)   | invalid                                 |
|                                         | [1, maxint)    | valid                                   |
| total calories                          | [1000, maxint) | invalid                                 |
|                                         | (0, 1000)      | valid                                   |
| fat ratio: (carb + protein) / fat > 0.5 | (0.5, maxint)  | invalid                                 |
|                                         | [0, 0.5]       | valid                                   |

N.B.
- sign of fat can't be 0 because it will be at denominator!
- since for last 2 conditions refers to value checked in the first 3 condition, we don't have to check all combinations, since some were already excluded BEFORE! otherways we would have also checked for total calories/fat ratio<0 equivalence class! (we are assuming that the function was implemented with parameters check and the start, and calories and fat ratio computed and checked later)->reasonable compromise to avoid huge numbers of rows.
- combination of 5 criteria valid/invalid=2^5=32

**Boundaries for method acceptableToEat**:

| Criterion        | Boundary values    |
| ---------------- | ------------------ |
| sign of carb     | -maxint, 0, maxint |
| sign  of protein | -maxint, 0, maxint |
| sign of fat      | -maxint, 0, maxint |
| total calories   | 0, 1000, maxint    |
| fat ratio        | 0, 0.5, maxint     |



 **Combination of predicates for method acceptableToEat**



| sign of carb | sign  of protein | sign of fat  | total calories | fat ratio | Valid/Invalid | Return Value | Description of the test case: example of input and output                          | JUnit test case                           |
| ------------ | ---------------- | ------------ | -------------- | --------- | ------------- | ------------ | ---------------------------------------------------------------------------------- | ----------------------------------------- |
| (-maxint, 0) | *                | *            | *              | *         | Invalid       | -            | T1(-5, 10, 10) -> error<br />Tb1(-1, 10, 10) -> error                              | T1 (testname containing those assertions) |
| *            | (-maxint, 0)     | *            | *              | *         | Invalid       | -            | T2(10, -5, 10) -> error<br />Tb2(10, -1, 10) -> error                              |                                           |
| *            | *                | (-maxint, 1) | *              | *         | Invalid       | -            | T3(10, 10, -5) -> error<br />Tb3(10, 10, 0) -> error                               |                                           |
| [0, maxint)  | [0, maxint)      | [1, maxint)  | <1000          | <=0.5     | Valid         | False        | T4(10,10,50) -> false                                                              |                                           |
| ''           | ''               | ''           | ''             | >0.5      | Valid         | True         | T5(10, 10, 5) -> true<br />Tb5(143, 100, 3) -> true (total calories = 999)         |                                           |
| ''           | ''               | ''           | >=1000         | <=0.5     | Valid         | False        | T6(10, 10, 50) -> false<br />Tb6(1000, 1000, 4001) -> false (fat ratio = 0.4999)   |                                           |
| ''           | ''               | ''           | ''             | >0.5      | Valid         | False        | T7(100, 100, 30) -> false<br />Tb7(1000, 1000, 3999) -> false (fat ratio = 0.5001) |                                           |

N.B.
- invalid=exception/error (depending on actual implementation could also return false/-1)
- valid=real return values (true or false)
- * all possible values
- " same value as line before
- Alternative format for TC(input1, input2; result), more similar to JUnit

