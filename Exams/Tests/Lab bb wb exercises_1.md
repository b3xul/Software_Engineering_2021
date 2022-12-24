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



### Method $triangleType$



**Criteria for method $triangleType$:**
	
- Side1: (minint, 0], [1, maxint) (2 intervals=2 exact boundary values! 0 and 1!)
- Side2: (minint, 0], [1, maxint)
- Side3: (minint, 0], [1, maxint)
- Side1+Side2>Side3: {true, false}
- Side1+Side3>Side2: {true, false}
- Side2+Side3>Side1: {true, false}
- Number of equal sides: {0}, {2}, {3} , !={0,2,3} (since this is a compound value, the last equivalence class can also be omitted because can't happen)
  
Other solution: compact table 
- (Side1+Side2>Side3)&&(Side1+Side3>Side2)&&(Side2+Side3>Side1)

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

| Criterion | Boundary values (only for numerical inputs! we don't consider also -maxint and maxint) |
| --------- | -------------------------------------------------------------------------------------- |
| Side1     | 0,1                                                                                    |
| Side2     | 0,1                                                                                    |
| Side3     | 0,1                                                                                    |

 **Combination of predicates for method push**

Suggestions: exclude invalid results before, then concentrate on valid ones, filling the table. Then write test cases for each one: N.B. 1 test case for each row+ 1 test case for each boundary

For wrong values (negative sides), the test is INVALID. If the function prototype has "throw Exception..", then we write -> throw exc.. otherways we can write -> error or -> -1 or false (depending on normal error condition of the function). In this case it was esplicited when it should have returned -1, so in that case it is a valid case, when -1 is returned.

| Side1       | Side2       | Side3       | C1    | C2    | C3    | Equal size | Valid/Invalid | Description of the test case                          |
| ----------- | ----------- | ----------- | ----- | ----- | ----- | ---------- | ------------- | ----------------------------------------------------- |
| (minint, 0] | *           | *           | *     | *     | *     | *          | I             | T1(-1,-1,-2) -> -1 <br> Tb1(0,-1,-2)->-1 (BOUNDARY 0) |
| *           | (minint, 0] | *           | *     | *     | *     | *          | I             | T2(3,-1,-2) -> -1 <br> Tb2(3,0,-2)->-1 (BOUNDARY 0)   |
| *           | *           | (minint, 0] | *     | *     | *     | *          | I             |
| *           | *           | *           | false | *     | *     | *          | I             | T4(10,2,1)->-1                                        |
| *           | *           | *           | *     | false | *     | *          | I             |
| *           | *           | *           | *     | *     | false | *          | I             |
| [1, maxint) | [1, maxint) | [1, maxint) | true  | true  | true  | 0          | V             | T7(2,3,4)->3                                          |
| [1, maxint) | [1, maxint) | [1, maxint) | true  | true  | true  | 2          | V             | T8(2,3,3)->2                                          |
| [1, maxint) | [1, maxint) | [1, maxint) | true  | true  | true  | 3          | V             | T9(3,3,3)->1                                          |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |
|             |             |             |       |       |       |            |


