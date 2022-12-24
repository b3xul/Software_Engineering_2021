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



### Method $computeMaxTime$



**Criteria for method $computeMaxTime$:**
	
- Winner_time: (mindouble, 0.0], (0.0, maxdouble) (2 intervals=2 boundary values! 0.0, 0.00001!!)
- Avg_speed: (mindouble, 0], (0.0, 30], (30, 35], (35, maxdouble)
- track_type: {A}, {B}, {C}, !={A,B,C}, ''

**Predicates for method push:**

| Criterion   | Predicate     |
| ----------- | ------------- |
| Criterion 1 | Predicate 1.1 |
|             | Predicate 1.2 |
|             | ...           |
| Criterion 2 | Predicate 2.1 |
|             | Predicate 2.2 |
|             | ...           |
| ...         | ...           |
|             |               |
|             |               |
|             |               |



**Boundaries for method push**:

| Criterion   | Boundary values (only for numerical inputs! we don't consider also -maxint and maxint) |
| ----------- | -------------------------------------------------------------------------------------- |
| Winner_time | 0.0, 0.00001                                                                           |
| Avg_speed   | 0.0, 0.00001, 30.0, 30.00001, 35.0, 35.00001                                           |

(for strings we could use string length for boundary values)

 **Combination of predicates for method push**

Suggestions: exclude invalid results before, then concentrate on valid ones, filling the table. Then write test cases for each one: N.B. 1 test case for each row+ 1 test case for each boundary

For wrong values (negative sides), the test is INVALID. If the function prototype has "throw Exception..", then we write -> throw exc.. otherways we can write -> error or -> -1 or false (depending on normal error condition of the function). In this case it was esplicited when it should have returned -1, so in that case it is a valid case, when -1 is returned.

| Winner_time      | Avg_speed       | track_type | Valid/Invalid | Description of the test case                              |
| ---------------- | --------------- | ---------- | ------------- | --------------------------------------------------------- |
| (mindouble, 0]   | *               | *          | I             | T1(-2.0,1,A) -> 0 <br> Tb1(0.0,1,A)->0 (BOUNDARY 0.0)     |
| *                | (mindouble, 0]  | *          | I             | T2(3.0,-2.0,A) -> 0 <br> Tb2(3.0,0.0,A)->0 (BOUNDARY 0.0) |
| *                | *               | !={A,B,C}  | I             | T3(3.0, 10.0,D) -> 0                                      |
| *                | *               | ''         | I             | T4(3.0, 10.0,'') -> 0                                     |
| (0.0, maxdouble) | (0.0, 30]       | A          | V             | T5(100.0, 20.0,A) -> 105 <br> tb5(100.0, 30,A)->105       |
| "                | (30, 35]        | A          | V             | T6(100.0, 31.0,A) -> 110 <br> tb5(100.0, 35,A)->110       |
| "                | (35, maxdouble) | A          | V             | T7(100.0, 36.0,A) -> 115                                  |
| "                | (0.0, 30]       | B          | V             | T8(100.0, 20.0,B) -> 120 <br> tb5(100.0, 30,B)->120       |
| "                | (30, 35]        | B          | V             | T9(100.0, 31.0,B) -> 125 <br> tb5(100.0, 35,B)->125       |
| "                | (35, maxdouble) | B          | V             | T10(100.0, 36.0,B) -> 135                                 |
| "                | *               | C          | V             | T11(100.0,34.0,C) -> 150                                  |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |
|                  |                 |            |               |                                                           |


