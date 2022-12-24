# Black Box Unit Tests - Exercise 2

# Method addItem

**Criteria for method addItem:**
- Validity of Item object
- Existence of Item object

**Predicates for method addItem:**
| Criterion                | Predicate |
| ------------------------ | --------- |
| Validity of Item object  | Valid     |
|                          | NULL      |
| Existence of Item object | Yes       |
|                          | No        |

!!!! We could also add validity checks to the addItem function that checks wheter the item has a valid itemCode, availability, description, name -> depending on the code we could add these checks or not, adding a third value: valid, invalid (for reasons..),NULL. If the logic is inside the setter, then the checks would not be needed here! With whitebox testing we can be more selective on the checks to perform. With blackbox testing we can just base our choice of the tests on the documentation available (if the method also throws an InvalidDescritption, it could mean that the code internally does that check!)

**Boundaries for method addItem**:
| Criterion | Boundary values |
| --------- | --------------- |
|           |                 |

 **Combination of predicates for method addItem**
| Validity of Item object | Existence of Item object | Valid/Invalid | Description of the test case: example of input and output                                              | JUnit test case |
| ----------------------- | ------------------------ | ------------- | ------------------------------------------------------------------------------------------------------ | --------------- |
| Valid                   | Yes                      | Invalid       | Item i1 = {i1, 0, "a", "a"}<br />addItem(i1);<br />addItem(i1);<br /><br />-> ItemAlreadyExists thrown |                 |
| ''                      | No                       | Valid         | Item i1 = {i1, 0, "a", "a"}<br />addItem(i1);<br /><br />-> Item added successfully                    |                 |
| NULL                    | *                        | Invalid       | T3(NULL; error)                                                                                        |                 |

The case NULL-Yes cannot exist, because a NULL object cannot exist.
Description is just pseudocode, while JUnit test case will contain the real test case!

# Method searchItem

**Criteria for method searchItem:**
- Validity of the String parameter
- Length of the String
- Existence of Item object

**Predicates for method searchItem:**

| Criterion                        | Predicate   |
| -------------------------------- | ----------- |
| Validity of the String parameter | Valid       |
|                                  | NULL        |
| Length of the String             | (0, maxint) |
|                                  | 0 ("")      |
| Existence of Item object         | Yes         |
|                                  | No          |

**Boundaries for method searchItem**:

| Criterion | Boundary values |
| --------- | --------------- |
|           |                 |

 **Combination of predicates for method searchItem**

| Validity of the String parameter | Length of the String | Existence of Item object | Valid/Invalid | Description of the test case: example of input and output                                        | JUnit test case |
| -------------------------------- | -------------------- | ------------------------ | ------------- | ------------------------------------------------------------------------------------------------ | --------------- |
| Valid                            | (0, maxint)          | Yes                      | Valid         | Item i1 = {i1, 0, "a", "a"}<br />addItem(i1);<br />searchItem("i1");<br /><br />-> item returned |                 |
| ''                               | ''                   | No                       | Invalid       | searchItem("i1")<br /><br />-> ItemNotExists                                                     |                 |
| *                                | 0                    | -                        | Invalid       | T3(""; error)                                                                                    |                 |
| NULL                             | -                    | -                        | Invalid       | T4(NULL; error)                                                                                  |                 |

Since ItemNotExists is an Exception/Error, the TC is invalid. In more mathematical functions the true and false results are both acceptable valid results.

# Method availabilityItem

**Criteria for method availabilityItem:**
- Validity of the String parameter
- Length of the String
- Existence of Item object

**Predicates for method push:**

| Criterion                        | Predicate   |
| -------------------------------- | ----------- |
| Validity of the String parameter | Valid       |
|                                  | NULL        |
| Length of the String             | (0, maxint) |
|                                  | 0 ("")      |
| Existence of Item object         | Yes         |
|                                  | No          |

**Boundaries for method availabilityItem**:

| Criterion | Boundary values |
| --------- | --------------- |
|           |                 |

 **Combination of predicates for method availabilityItem**

| Validity of the String parameter | Length of the String | Existence of Item object | Valid/Invalid | Description of the test case: example of input and output                                                                  | JUnit test case |
| -------------------------------- | -------------------- | ------------------------ | ------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Valid                            | (0, maxint)          | Yes                      | Valid         | Item i1 = {i1, 0, "a", "a"}<br />addItem(i1);<br />availabilityItem("i1");<br /><br />-> availability of the item returned |                 |
| ''                               | ''                   | No                       | Invalid       | availabilityItem("i1")<br /><br />-> ItemNotExists                                                                         |                 |
| *                                | 0                    | -                        | Invalid       | T3(""; error)                                                                                                              |                 |
| NULL                             | -                    | -                        | Invalid       | T4(NULL; error)                                                                                                            |                 |

# Method subtractItem

**Criteria for method subtractItem:**
	

- Validity of the String parameter
- Length of the String
- Existence of Item object
- Availability of Item object

**Predicates for method subtractItem:**

| Criterion                        | Predicate               |
| -------------------------------- | ----------------------- |
| Validity of the String parameter | Valid                   |
|                                  | NULL                    |
| Length of the String             | (0, maxint)             |
|                                  | 0 ("")                  |
| Existence of Item object         | Yes                     |
|                                  | No                      |
| Availability of Item object      | Yes (availability >= 1) |
|                                  | No (availability = 0)   |

<0 can't exist because then the object would be invalid! (checked in setter function)

**Boundaries for method subtractItem**:

| Criterion                   | Boundary values |
| --------------------------- | --------------- |
| Availability of Item object | 0,1             |

 **Combination of predicates for method subtractItem**

| Validity of the String parameter | Length of the String | Existence of Item object | Availability of Item object | Valid/Invalid | Description of the test case: example of input and output | JUnit test case |
| -------------------------------- | -------------------- | ------------------------ | --------------------------- | ------------- | --------------------------------------------------------- | --------------- |
| Valid                            | (0, maxint)          | Yes                      | >= 1                        | Valid         | T0 -> availability returned                               |                 |
| ''                               | ''                   | Yes                      | =0                          | Invalid       | T1 -> throws ItemNotAvailable                             |                 |
| ''                               | ''                   | No                       | -                           | Invalid       | T2 -> throws ItemNotExists                                |                 |
| *                                | 0                    | -                        | -                           | Invalid       | T3(""; error)                                             |                 |
| NULL                             | -                    | -                        | -                           | Invalid       | T4(NULL; error)                                           |                 |

Dash - means that if the item does not exist, we are not able to check its availability. If string is invalid, we cannot check its length!

# Method addQtyToItem

**Criteria for method addQtyToItem:**
	

- Validity of the String parameter
- Length of the String
- Existence of Item object
- Availability of Item object
- Sign of the qty_to_add parameter

**Predicates for method addQtyToItem:**

| Criterion                        | Predicate |
| -------------------------------- | --------- |
| Validity of the String parameter | Valid     |
|                                  | NULL      |
| Length of the String             | > 0       |
|                                  | = 0 ("")  |
| Existence of Item object         | Yes       |
|                                  | No        |
| Sign of the qty_to_add_parameter | >=0       |
|                                  | <0        |

**Boundaries for method addQtyToItem**:

| Criterion                        | Boundary values |
| -------------------------------- | --------------- |
| Availability of Item object      | 0,1             |
| Sign of the qty_to_add_parameter | 0,1             |

 **Combination of predicates for method addQtyToItem**

| Validity of the String parameter | Length of the String | Existence of Item object | Sign of the qty_to_add parameter | Valid/Invalid | Description of the test case: example of input and output | JUnit test case |
| -------------------------------- | -------------------- | ------------------------ | -------------------------------- | ------------- | --------------------------------------------------------- | --------------- |
| Valid                            | >0                   | Yes                      | <0                               | Invalid       | T0 -> error                                               |                 |
| ''                               | ''                   | ''                       | >=0                              | Valid         | T1 -> availability added                                  |                 |
| ''                               | ''                   | No                       | -                                | Invalid       | T2 -> throws ItemNotExists                                |                 |
| *                                | 0                    | -                        | -                                | Invalid       | T3(""; error)                                             |                 |
| NULL                             | -                    | -                        | -                                | Invalid       | T4(NULL; error)                                           |                 |

# Method subtractQtyToItem

**Criteria for method subtractQtyToItem:**
	

- Validity of the String parameter
- Length of the String
- Existence of Item object
- Availability after subtraction
- Sign of the qty_to_add parameter

**Predicates for method subtractQtyToItem:**

| Criterion                             | Predicate |
| ------------------------------------- | --------- |
| Validity of the String parameter      | Valid     |
|                                       | NULL      |
| Length of the String                  | > 0       |
|                                       | = 0 ("")  |
| Existence of Item object              | Yes       |
|                                       | No        |
| Sign of the qty_to_subtract_parameter | >=0       |
|                                       | <0        |
| Availability after subtraction        | <0        |
|                                       | >=0       |

**Boundaries for method subtractQtyToItem**:

| Criterion                             | Boundary values |
| ------------------------------------- | --------------- |
| Availability of Item object           | 0,1             |
| Sign of the qty_to_subtract_parameter | 0,1             |

 **Combination of predicates for method subtractQtyToItem**

| Validity of the String parameter | Length of the String | Existence of Item object | Sign of the qty_to_add parameter | Availability after subtraction | Valid/Invalid | Description of the test case: example of input and output | JUnit test case |
| -------------------------------- | -------------------- | ------------------------ | -------------------------------- | ------------------------------ | ------------- | --------------------------------------------------------- | --------------- |
| Valid                            | >0                   | Yes                      | <0                               | *                              | Invalid       | T0 -> error                                               |                 |
| ''                               | ''                   | ''                       | >=0                              | <0                             | Invalid       | T1 -> throw ItemNotAvailable                              |                 |
| ''                               | ''                   | ''                       | ''                               | >=0                            | Valid         | T2 -> availability subtracted                             |                 |
| ''                               | ''                   | No                       | -                                | -                              | Invalid       | T3 -> throws ItemNotExists                                |                 |
| *                                | 0                    | -                        | -                                | -                              | Invalid       | T4(""; error)                                             |                 |
| NULL                             | -                    | -                        | -                                | -                              | Invalid       | T5(NULL; error)                                           |                 |

