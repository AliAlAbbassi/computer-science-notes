# Describing Syntax and Semantics
This chapter begins by defining the terms syntax and semantics.

The syntax of a programming language is the form of its expressions, statements, and program units. Its semantics is the meaning of those expressions, statements, and program units.

Formal descriptions of the syntax of programming languages, for simplicity’s sake, often do not include descriptions of the lowest- level syntactic units. These small units are called lexemes. The description of lexemes can be given by a lexical specification, which is usually separate from the syntactic description of the language. The lexemes of a programming language include its numeric literals, operators, and special words, among others. One can think of programs as strings of lexemes rather than of characters.

##### Lexems
Lexemes are partitioned into groups— for example, the names of variables, methods, classes, and so forth in a programming language form a group called identifiers. Each lexeme group is represented by a name, or token. So, a token of a language is a category of its lexemes. For example, an identifier is a token that can have lexemes, or instances, such as sum and total. In some cases, a token has only a single possible lexeme. For example, the token for the arithmetic operator symbol + has just one possible lexeme. Consider the following Java statement:
```
index = 2 * count + 17;
```
The lexemes and tokens of this statement are
```
Lexemes		Tokens 
index		identifier 
= 			equal_sign 
2 			int_literal
* 			mult_op 
count 		identifier 
+ 			plus_op 
17 			int_literal 
; 			semicolon
```

#### Language Generators
A language generator is a device that can be used to generate the sentences of a language. We can think of the generator as having a button that produces a sentence of the language every time it is pushed. Because the particular sentence that is produced by a generator when its button is pushed is unpredictable, a generator seems to be a device of limited usefulness as a language descriptor. However, people prefer certain forms of generators over recognizers because they can more easily read and understand them. By contrast, the syntax-checking portion of a compiler (a language recognizer) is not as useful a language description for a programmer because it can be used only in trial-and-error mode. 

#### Fundamentals
##### Metalanguage
A metalanguage is a language that is used to describe another language. BNF is a metalanguage for programming languages. 

BNF uses abstractions for syntactic structures. A simple Java assignment statement, for example, might be represented by the abstraction (pointed brackets are often used to delimit names of abstractions). The actual definition of can be given by
```
<assign> -> <var> = <expression>
```

##### Grammars and Derivations
A grammar is a generative device for defining languages. The sentences of the language are generated through a sequence of applications of the rules, beginning with a special nonterminal of the grammar called the start symbol. This sequence of rule applications is called a derivation. In a grammar for a complete programming language, the start symbol represents a complete program and is often named . The simple grammar shown in Example 3.1 is used to illustrate derivations.

###### A Grammar for a Small Language
![](https://cdn.discordapp.com/attachments/845561994022879264/889950006411411456/unknown.png)


The language described by the grammar of Example 3.1 has only one statement form: assignment. A program consists of the special word begin, followed by a list of statements separated by semicolons, followed by the special word end. An expression is either a single variable or two variables separated by either a + or - operator. The only variable names in this language are A, B, and C. 

A derivation of a program in this language follows:
![](https://cdn.discordapp.com/attachments/845561994022879264/889954856985579580/unknown.png)

##### Parse Trees
Parse trees naturally describe the hierarchical syntactic structure of the sentences of the languages they define. These hierarchical structures are called parse trees.

Every internal node of a parse tree is labeled with a nonterminal symbol; every leaf is labeled with a terminal symbol. Every subtree of a parse tree describes one instance of an abstraction in the sentence

##### Ambiguity
A grammar that generates a sentential form for which there are two or more distinct parse trees is said to be ambiguous

There are several other characteristics of a grammar that are sometimes useful in determining whether a grammar is ambiguous.1 They include the following: (1) if the grammar generates a sentence with more than one leftmost derivation and (2) if the grammar generates a sentence with more than one rightmost derivation.