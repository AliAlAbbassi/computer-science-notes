# Preliminaries

### Reasons for studying COP
- Increased capacity to express ideas.
- Improved background for choosing appropriate languages
- Increased ability to learn new languages
- Better understanding of the significance of implementation
- Better use of languages that are already known
- Overall advancement of computing.

### Language Evaluation Criteria

#### Readability
Because ease of maintenance is determined in large part by the readability of programs, readability became an important measure of the quality of programs and programming languages. This was an important juncture in the evolution of programming languages. There was a distinct crossover from a focus on machine orientation to a focus on human orientation. 

Readability must be considered in the context of the problem domain. For example, if a program that describes a computation is written in a language not designed for such use, the program may be unnatural and convoluted, making it unusually difficult to read.
#### Overall Simplicity
The overall simplicity of a programming language strongly affects its readability.

A second complicating characteristic of a programming language is feature multiplicity— that is, having more than one way to accomplish a particular operation. 

For example, in Java, a user can increment a simple integer variable in four different ways: 
```
count = count + 1 
count += 1 
count++ 
++count
```
A third potential problem is operator overloading, in which a single operator symbol has more than one meaning. Although this is often useful, it can lead to reduced readability if users are allowed to create their own overloading and do not do it sensibly.

For example, it is clearly acceptable to overload + to use it for both integer and floating-point addition.

#### Overall Simplicity
Orthogonality in a programming language means that a relatively small set of primitive constructs can be combined in a relatively small number of ways to build the control and data structures of the language.