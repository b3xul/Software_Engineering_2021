# criteria
| Criterion                                                                                      | Predicate             | Valid/Invalid |
| ---------------------------------------------------------------------------------------------- | --------------------- | ------------- |
| age                                                                                            | (minint, -1]          | invalid       |
|                                                                                                | [0, 5]                | valid         |
|                                                                                                | [6, 65]               | valid         |
|                                                                                                | [66, maxint)          | valid         |
| income                                                                                         | (mindouble, 0)        | invalid       |
|                                                                                                | [0, 8263.57)          | valid         |
|                                                                                                | [8263.57, 36151.98)   | valid         |
|                                                                                                | [36151.98, maxdouble) | valid         |
| isEmployed                                                                                     | true                  | valid         |
|                                                                                                | false                 | valid         |
| eligible: ((age<6 OR age>65)&&income<36151.98&&isEmployed) OR (income<8263.57 && !isEmployed)) | true                  | valid         |
|                                                                                                | false                 | valid         |




# combinations

| isEmployed | age                    | income                                       | eligible | V/I | Test Case                                                                                    |
| ---------- | ---------------------- | -------------------------------------------- | -------- | --- | -------------------------------------------------------------------------------------------- |
| *          | (minint, -1]           | *                                            |          | I   | T1(-2,3000,false)->error<br>T1b(-1,3000,false)->error                                        |
| *          | *                      | (mindouble, 0)                               |          | I   | T1(3,-500.0,false)->error<br>T1b(3,-0.01,false)->error                                       |
| *          | [0, 5] OR [66, maxint) | [0, 8263.57) OR [8263.57, 36151.98)          | True     | V   | T3(3,3000,false)->1<br>T3b(0,0,false)->1<br>T3c(5,3151.97,false)->1<br>T4c(66,3000,false)->1 |
| *          | [6, 65]                | *                                            | False    | V   | T4(15,3000,false)->0                                                                         |
| *          | *                      | [36151.98, maxdouble)                        | False    | V   | T5(15,30000000,false)->0                                                                     |
| False      | *                      | [0, 8263.57)                                 | True     | V   | T6(15,3000,true)->1 <br>T6b(15,8263.56,true)->1                                              |
| False      | *                      | [8263.57, 36151.98) OR [36151.98, maxdouble) | False    | V   | T7(15,10000,true)->0<br>T7b(15,8263.57,true)->0                                              |
|            |                        |                                              |          |     |                                                                                              |
