# Design Document 

Authors: B3xul

Date: 17/06/2021

Version: 1.0

# Contents

- [Design Document](#design-document)
- [Contents](#contents)
- [Instructions](#instructions)
- [WorkFlow:](#workflow)
- [Notes:](#notes)
- [High level design](#high-level-design)
- [Low level design](#low-level-design)
- [Verification traceability matrix](#verification-traceability-matrix)
- [Verification sequence diagrams](#verification-sequence-diagrams)

# Instructions

The design must satisfy the Official Requirements document 

# WorkFlow:
How to make a good Design 

1. Read requirements 
2. Decide on the architecture to use Layered Model (3-tier architecture),(Repository, Microkernel, , Client-Server,  Model-View-Controller, Pipes and Filters, Microservices, Broker 
3. Create the package diagram 
4. For each package create its UML Class Diagram: 
   1. From Glossary and Context diagram extract classes that we would need in the code
   2. Add other classes that may be useful 
   3. Inside each class insert attributes (type, privacy), methods (privacy, return value, arguments, type of arguments), add needed getters and setters, choose sort algorithm(or other algorithms), decide which classes need persistance, choose relationship with other classes: 
   4. Decide direction of arrows between 2 classes (which of the 2 keeps reference of the other. 
      1. If 1 reference: attribute+set method. If more reference we first choose the collection to use:array,list,map.., and then we add the collection+add method. 
      2. If relationship many to many we could also decide to create an external map containing IDs of the 2 classes and then save the reference to that map in both classes.

# Notes:
- Constructor, Getter, Setter not needed since they are defaults, they do not add useful information to the diagram.
- To manage hardware we need a class for each device driver that we need to manage. (Also if external!) (EZShop)
- Using a Java code generator it automatically creates classes starting from the class diagram!
- Separate 3 transaction functions because they are logically divided and they have different parameters
- Administrator class would be useful because they have their own account and pwd attributes
- How to manage different permissions (colleagues that could do some of the administrator functions): add capabilities-administrator class that manages the capability table that tells which account can or can't do any operation
- Transactions could be directly connected to LaTazza to semplify the produceTransactionReport() function.
- How to implement CapsuleTypes? Since there is a search function we need search to be fast! We could use an HashTree! CapsuleTypes will contain only references to the Capsule Type!
- We can add arrows to indicate the direction of the relationship (LaTazza->CapsuleType)
- PersonalAccount could be merged to Colleague inserting the balance directly in the colleague, since there is a 1 to 1 relationship. Also with LaTazza and LaTazzaAccount! Every time there is a 1 to 1 relationship we could merge the classes.
- Methods must be close to the data (functions in LaTazza, not in administrator)
- Better 1 method for each different transaction because different parameters needed
- Persistance is at the model level typically! All classes in model/data tier. How to do persistance? Tipically database more effective in the long run! Considering persistance we should not merge LaTazza and LaTazzaAccount because we split better the model from the logic, and we can just have persistance in the model classes.
- Consider for each UseCase if we can do them! ex. manageConsumption(){showCapsuleType(); (GUI)->admin select capsule type-> ct=searchCapsuleType();showColleagues() MUST BE ADDED!->GUI->admin selects colleague->c=searchColleague();c.getPersonalAccount.changeBalance(-ct.getPrice);ct.changeQuantity(-1);}
- Executing scenarios we already check the traceability matrix
- Then you can generate code and compile it


# High level design 

<discuss architectural styles used, if any>
<report package diagram>

Architecture:
- Stand-alone (not client-server)
- Model View Controller
- 3-tier layered architecture
- too simple to apply microservices

1. Application logic distinct from Model
```
@startuml

package "GUI" as GUI
note "View,Controller in GUI" as N1
N1--GUI

package "Application logic tier"
package "Model tier" as Model
note "Model in Model tier" as N2
N2--Model

@enduml
```
2. Logic and model together (simple case)
```
@startuml

package "GUI" as GUI
note "View,Controller in GUI" as N1
N1--GUI

package "Application logic + Model tier" as All
note "Model in All" as N2
N2--All

@enduml
```

# Low level design

<for each package, report class diagram>

- For the GUI Package after Balsamiq prototype we will use Java Swing Framework (or any GUI builder) that automatically implements the classes related to the GUI that we want to create.

- MVC Controller could be in the GUI package or in the Application logic.

- For the Application logic + Model tier Package instead we need the UML Class Diagram

```
@startuml
rectangle applicationLogic{
class LaTazza{
    -Colleagues
    -LaTazzaAccount
    -CapsuleTypes

    showColleagues()
    addColleague()
    modifyColleague()

    addCapsuleType()
    showCapsuleType()
    searchCapsuleType()

    manageBoxPurchase()
    manageRecharge()
    manageConsumption()
    produceConsumptionReportForColleague()
    produceTransactionsReport()
}
}
note "could also contain the Controller" as N
N-- LaTazza

rectangle Model+Data{
class LaTazzaAccount{
    -balance: double
    +changeBalance(amount: double)
    -Transactions
}
class CapsuleType{
    -ID
    -name
    -price
    -quantity
    +changeQuantity()
}
class Colleague{
    -name
    -surname
    -PersonalAccount
}
class Administrator{
    -accountname
    -password
}
class PersonalAccount{
    -balance
    changeBalance()
}


class Transaction{
    -date
    -amount
    -type
    -PersonalAccount
}
class BoxPurchase{
    -quantity
}
class Consumption
class Recharge


Colleague"*"<-- LaTazza
LaTazzaAccount<-- LaTazza
CapsuleType"*"<-- LaTazza
Transaction"*"-- LaTazza
CapsuleType--"*" Consumption
CapsuleType-- "*" BoxPurchase
LaTazzaAccount--"*" Consumption
LaTazzaAccount-- "*" BoxPurchase
Colleague--PersonalAccount
Transaction"*"--PersonalAccount
BoxPurchase--|>Transaction
Consumption--|>Transaction
Recharge--|>Transaction

Administrator--|>Colleague
}
@enduml
```

# Verification traceability matrix

\<for each functional requirement from the requirement document, list which classes concur to implement it>











# Verification sequence diagrams 
\<select key scenarios from the requirement document. For each of them define a sequence diagram showing that the scenario can be implemented by the classes and methods in the design>

