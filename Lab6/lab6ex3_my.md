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
	

- Duration (minutes used)
- minRate (cost per minute in cents)
- minRate2 (cost per minute in cents)
- if(duration<=30) totalFee=0
- else if(duration>30 && duration<=90) totalFee=(duration-30)*minRate
- else totalFee=60*minRate+(duration-90)*minRate2 
  

**Predicates for method computeFee:**

| Criterion     | Predicate    | Result  |
| ------------- | ------------ | ------- |
| duration sign | (-maxint, 0) | Invalid |
|               | (0, 30]      | valid   |
|               | (30, 90]     | valid   |
|               | (0, maxint)  | valid   |
| minRate       | (-maxint, 0) | Invalid |
|               | (0, maxint)  | valid   |
| minRate2      | (-maxint, 0) | Invalid |
|               | (0, maxint)  | valid   |




**Boundaries for method computeFee**:

| Criterion     | Boundary values        |
| ------------- | ---------------------- |
| duration sign | -maxint,0,30,90,maxint |
| minRate       | -maxint,0,maxint       |
| minRate2      | -maxint,0,maxint       |


 **Combination of predicates for method computeFee**

| duration sign | minRate     | minRate2     | Valid/Invalid | Description of the test case                                 | JUnit test case |
| ------------- | ----------- | ------------ | ------------- | ------------------------------------------------------------ | --------------- |
| (0, maxint)   | (0, maxint) | (0, maxint)  | Valid         | T1((0,5,10);0)<br /> T1b((3,5,10);0)<br /> T1c((30,5,10);0)  |                 |
| "             | "           | "            | Valid         | T2((31,5,10);0)<br />T2b((33,5,10); <br /> T2c((90,5,10);15) |                 |
| "             | "           | "            | Valid         | T3((93,5,10);<br /> T3b((91,5,10);0)                         |                 |
| *             | *           | (-maxint, 0) | Invalid       | T4((93,5,-10);ERROR)                                         |                 |
| *             | (-maxint,0) | *            | Invalid       | T4((93,-5,10);ERROR)                                         |                 |
| (-maxint, 0)  | *           | *            | Invalid       | T4((-93,5,10);ERROR)                                         |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |
|               |             |              |               |                                                              |                 |


