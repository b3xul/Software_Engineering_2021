# Unit Testing Documentation template

Authors:

Date:

Version:





# Black Box Unit Tests

```
<Define here criteria, predicates and the combination of predicates for each function of each class.
Define test cases to cover all equivalence classes and boundary conditions.
In the table, report the description of the black box test case and the correspondence with the JUnit black box test case name/number>
```



### Method $computeFee$



**Criteria for method $computeFee$:**
	

- basePrice
- n_passengers
- n_over18
- n_under15

we either add the criteria - n_passengers >= n_over18 + n_under15 (validity check) or we manually check numbers

**Predicates for method computeFee:**

| Criterion    | Predicate       | Result            |
| ------------ | --------------- | ----------------- |
| basePrice    | (-maxdouble, 0] | Invalid           |
|              | (0, maxdouble)  | valid             |
| n_passengers | (-maxint, 0]    | Invalid           |
|              | 1               | valid (non offer) |
|              | [2, 5]          | valid (offer)     |
|              | [6, maxint)     | invalid           |
| n_over18     | (-maxint, 0)    | Invalid           |
|              | 0               | valid (no offer)  |
|              | [1, 5]          | valid (offer)     |
|              | [6, maxint)     | invalid           |
| n_under15    | (-maxint, 0)    | Invalid           |
|              | [1, 4]          | valid (offer)     |
|              | 5               | valid (no offer)  |
|              | [6, maxint)     | invalid           |




**Boundaries for method computeFee**:

| Criterion    | Boundary values          |
| ------------ | ------------------------ |
| basePrice    | -maxdouble,0,maxdouble   |
| n_passengers | -maxint,0,1,2,5,6,maxint |
| n_over18     | -maxint,0,1,5,6,maxint   |
| n_under15    | -maxint,0,1,4,5,6,maxint |


 **Combination of predicates for method computeFee**

| basePrice       | n_passengers | n_over18     | n_under15    | Valid/Invalid    | Description of the test case                                                                         | JUnit test case |
| --------------- | ------------ | ------------ | ------------ | ---------------- | ---------------------------------------------------------------------------------------------------- | --------------- |
| (0, maxdouble)  | [2, 5]       | [1, 5]       | [1, 4]       | Valid (offer)    | T1((5.0,3,1,2);5.0)<br /> T1b((5.0,2,1,1);5.0)<br /> T1c((5.0,5,1,4);5.0)<br />T1d((5.0,5,4,1);15.0) |                 |
| "               | *            | 0            | [1, 5]       | Valid (no offer) | T2((5.0,3,0,5);5.0)<br /> T2b((5.0,2,1,1);5.0)<br />                                                 |                 |
| "               | [1, 5]       | *            | 0            | Valid (no offer) | T3((5.0,1,1,0);5.0))                                                                                 |                 |
| "               | 1            | *            | *            | Valid (no offer) | T3((5.0,1,1,0);5.0))                                                                                 |                 |
| *               | *            | *            | (-maxint, 0) | Invalid          | T4((5.0,3,1,-1);ERROR)                                                                               |                 |
| *               | *            | (-maxint, 0) |              | Invalid          | T5((5.0,3,-1,2);ERROR)                                                                               |                 |
| *               | (-maxint,0]  | *            |              | Invalid          | T6((5.0,0,1,2);ERROR)                                                                                |                 |
| (-maxdouble, 0] | *            | *            |              | Invalid          | T7((0.0,3,1,2);ERROR)                                                                                |                 |
| *               | *            | *            | [6, maxint)  | Invalid          | T8((5.0,3,1,6);ERROR)                                                                                |                 |
| *               | *            | [6, maxint)  |              | Invalid          | T9((5.0,3,6,2);ERROR)                                                                                |                 |
| *               | [6, maxint)  | *            |              | Invalid          | T10((5.0,6,1,2);ERROR)                                                                               |                 |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |
|                 |              |              |              |                  |                                                                                                      |


