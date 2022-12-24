

# Black Box Unit Tests - Exercise 4

### Method computeFee



**Criteria for method computeFee:**
	

- duration
- sign of minRate
- sign of minRate2



**Predicates for method computeFee:**

| Criterion        | Predicate    |
| ---------------- | ------------ |
| duration         | [minint, -1] |
|                  | [0,30]       |
|                  | [31, 90]     |
|                  | [91, maxint] |
| sign of minrate  | [minint, 0)  |
|                  | [0, maxint]  |
| sign of minrate2 | [minint, 0)  |
|                  | [0, maxint]  |

**Boundaries for method push**:

| Criterion        | Boundary values      |
| ---------------- | -------------------- |
| duration         | 0, 1, 30, 31, 90, 91 |
| sign of minrate  | -1, 0, 1             |
| sign of minrate2 | -1, 0, 1             |



 **Combination of predicates for method computeFee**



| duration     | sign of minrate | sign of minrate2 | Valid/Invalid | Description of the test case: example of input and output                                                      | JUnit test case |
| ------------ | --------------- | ---------------- | ------------- | -------------------------------------------------------------------------------------------------------------- | --------------- |
| [minint, 0)  | *               | *                | I             | T1(-10, 10, 10) -> error<br />T1b(-1, 10, 10) -> error                                                         |                 |
| *            | [minint, 0)     | *                | I             | T2(10, -10, 10) -> error<br />T2b(10, -1, 10) -> error                                                         |                 |
| *            | *               | [minint, 0)      | I             | T3(10, 10, -10) -> error<br />T3b(10, 10, -1) -> error                                                         |                 |
| [0, 30]      | [0, maxint]     | [0, maxint]      | V             | T4(10, 10, 10) -> 0.0<br />T4b1(0, 10, 10) -> 0.0<br />T4b2(1, 10, 10) -> 0.0;<br />T4b3(30, 10, 10) -> 0.0    |                 |
| [31, 90]     | ''              | ''               | V             | T5(60, 10, 10) -> 300<br />T5b1(31, 10, 10) -> 10<br />T5b2(90, 10, 10) -> 600                                 |                 |
| [91, maxint] | ''              | ''               | V             | T6(100, 10o, 20) -> 800<br />T6b1(91, 10, 20) -> 620<br />T6b2(100, 0, 20) -> 200<br />T6b3(100, 10, 0) -> 600 |                 |




