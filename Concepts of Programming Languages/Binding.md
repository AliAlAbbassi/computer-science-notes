# Binding
keywords: #binding #copl

A binding is an association between an **attribute** and an **entity**, such as between a variable and its type or value, or between an operation and a symbol. The time at which a binding takes place is called binding time.

Consider this piece of code
```
count = count + 5;
```

Some of the bindings and their binding times for the parts of this assignment statement are as follows: 
- The type of count is bound at compile time. 
- The set of possible values of count is bound at compiler design time. 
- The meaning of the operator symbol + is bound at compile time, when the types of its operands have been determined. 
- The internal representation of the literal 5 is bound at compiler design time. 
- The value of count is bound at execution time with this statement.

### Binding of Attributes to Variables
A binding is **static** if it first occurs before run time begins and remains unchanged throughout program execution. If the binding first occurs during run time or can change in the course of program execution, it is called **dynamic**.

### Type Binding
##### Static Type Binding 
An explicit declaration is a statement in a program that lists variable names and specifies that they are a particular type. An implicit declaration is a means of associating variables with types through default conventions, rather than declaration statements. In this case, the first appearance of a variable name in a program constitutes its implicit declaration. Both explicit and implicit declarations create static bindings to types. 

##### Type Inference 
```
let sum = 0
let total = 0.0
let name = "Bruce Baby"
```
Idea is to let the programming language infere the type of the variable by looking at it's value

##### Dynamic Type Binding 
Type of var can be changed i.e let in Js