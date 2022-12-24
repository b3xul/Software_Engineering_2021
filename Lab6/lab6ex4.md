

# Black Box Unit Tests - Exercise 3

### Method computeFee



**Criteria for method computeFee:**
	

- Sign of basePrice
- number of passengers
- number of over 18
- number of under 15
- n_passengers >= n_over18 + n_under15 (validity check)



**Predicates for method push:**

| Criterion                            | Predicate       |
| ------------------------------------ | --------------- |
| sign of base price                   | (-maxdouble, 0] |
|                                      | (0, maxdouble)  |
| number of passengers                 | [minint, 1]     |
|                                      | [2, 5]          |
|                                      | [6, maxint]     |
| number of over 18                    | [minint, -1]    |
|                                      | {0}             |
|                                      | [1, 5]          |
|                                      | [6, maxint]     |
| number of under 15                   | [minint, -1]    |
|                                      | [0, 5]          |
|                                      | [6, maxint]     |
| n_passengers >= n_over18 + n_under15 | false           |
|                                      | true            |



**Boundaries for method push**:

| Criterion          | Boundary values    |
| ------------------ | ------------------ |
| sign of baseprice  | -0.0001, 0, 0.0001 |
| number of over18   | -1,0,1,5,6         |
| number of under 15 | -1,0,1,5,6         |



 **Combination of predicates for method push**



| sign of base price | number of passengers | number of over 18 | number of under 15 | n_passengers >= n_over18 + n_under15 | Valid/Invalid | Description of the test case: example of input and output    | JUnit test case |
| ------------------ | -------------------- | ----------------- | ------------------ | ------------------------------------ | ------------- | ------------------------------------------------------------ | --------------- |
| [mindouble, 0]     | *                    | *                 | *                  | *                                    | I             | T1(-10.0, 3, 1, 1) -> error<br />T1b(0, 3, 1, 1) -> error    |                 |
| *                  | [minint, 1]          | *                 | *                  | *                                    | I             | T2(10.0, -5, 2, 2) -> error<br />T2b(10.0, 1, 2, 2) -> error |                 |
| *                  | *                    | [minint, -1]      | *                  | *                                    | I             | T3(10.0, 5, -2, 2) -> error<br />T3b(10.0, 5, -1, 2) -> error |                 |
| *                  | *                    | *                 | [minint, -1]       | *                                    | I             | T4(10.0, 5, 2 -2) -> error<br />T4b(10.0, 5, 2, -1) -> error |                 |
| (0, maxdouble)     | [2, 5]               | 0                 | [0, 5]             | false                                | I             | T5(10.0, 3, 0, 4) -> erro''r                                 | ''              |
| ''                 | ''                   | ''                | ''                 | true                                 | V             | T6(10.0, 2, 0, 2) -> 2*10.0 = 20.0<br />T6b1(0.00001, 3, 0, 2) -> 3 * 0.000001<br />T6b2(10.0,2,0,2) -> 2 * 10.0<br />T6b3(10.0, 3, 0, 0) -> 3*10.0<br />T6b4(10.0, 5, 0, 5) -> 5 * 10.0 |                 |
| ''                 | ''                   | [1, 5]            | [0, 5]             | false                                | I             | T7(10.0,2,2,3) -> error                                      |                 |
| ''                 | ''                   | ''                | ''                 | true                                 | V             | T8(10.0, 4, 2, 2) -> 20.0<br />T8b1(10.0, 4, 1, 2) -> 20.0<br />T8b2(10.0, 5, 5, 0) -> 50.0 |                 |
| *                  | [6, maxint]          | *                 | *                  | *                                    | I             | T9(10.0, 7, 2, 2) -> error<br />T9b(10.0, 6, 2, 2) -> error  |                 |
| *                  | *                    | [6, maxint]       | *                  | *                                    | I             | T10(10.0, 2, 7, 2) -> error<br />T10b(10.0, 2, 6, 2) -> error |                 |
| *                  | *                    | *                 | [6, maxint]        | *                                    | I             | T11(10.0, 2, 2, 7) -> error<br />T11b(10.0, 2, 2, 6) -> error |                 |




