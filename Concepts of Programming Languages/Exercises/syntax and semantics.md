# review questions

##### Define lexem and token 
lexeme is a low level syntactic unit. It can be a number, special word, or operator. A program is a string of lexems instead of characters

token is a category of lexems

##### How are programming languages formally defined?
they're formally defined by recognition and generation

With the recognition method, a mechanism R, called the recognition device, is constructed to read strings of characters from the alphabet *insert alphabet symbol*. R would indicate whether a given input string was or was not in L.

A language generator is a device that can be used to generate the sentences of a language

##### In which form is the programming language syntax commonly described?
PLs syntax is commonly described in grammars, i.e context free grammars and backus-naur form

##### What is a metalanguage?
A metalangugae is a langugae used to described another language. BNF is a metalanguage for programming languages.

##### What is a derivation in the context of grammar?
A derivation of a string for a grammar is **a sequence of grammar rule applications that transform the start symbol into the string**. A derivation proves that the string belongs to the grammar's language. A derivation is fully determined by giving, for each step: the rule applied in that step.

##### What is an ambiguous grammar?
A grammar that generates a sentential form for which there are two or more distinct parse trees is said to be ambiguous.

# Problem Set
##### Q1
The two mathematical models of language description are generation and recognition. Describe how each can define the syntax of a programming language.

##### A
Recognition defines the syntax of a programming language by constructing a mechanism R, called a recognition device, which would read strings of characters from the alphabet

Generation defines the syntax of a programming language by generating a sentence of the language  

##### Q2
Write EBNF descriptions for the following: 
- A Java class definition header statement 
- A Java method call statement 
- A C switch statement 
- A C union definition 
- C float literals

##### A 
class header statement: 
```
public class A extends B implements C, D
<method_head> -> [public] [(abstract | final)] [class<id>] [extends<id>] [implements <id> {, <id>}] 
```

java switch statement:
```
switch (a+b) {
	case 1:
		x=7;
		break;
	case 2:
		x=8;
		break;
	default:
		x=9;
		break;
}
```

```
<switch_stmnt> -> switch(<int expr>) {
	case <int const> : {<stmt> ;}
	{case <int const>: {stmt ;}}
	[default: {<stmt> ;}]
}
```

##### Q3
Rewrite the BNF of Example 3.4 to give + precedence over * and force + to be right associative.

```
<assign> -> <id> = <expr>
<id> -> A | B | C
<expr> -> <expr> + <term> | <term>
<term> -> <term> * <factor> | <factor>
<factor> -> (<expr>) | <id>
```

##### A 
```
<assign> -> <id> = <expr>
<id> -> A | B | C
<expr> -> <expr> * <term> | <term>
<term> -> <term> + <factor> | <factor>
<factor> -> (<expr>) | <id>
```

##### Q4
Rewrite the BNF of Example 3.4 to add the ++ and -- unary operators of Java.

##### A 
```
<assign> -> <id> = <expr>
<id> -> A | B | C
<expr> -> <expr> * <term> | <term>
<term> -> <term> + <factor> | <factor>
<factor> -> (<expr>) | <id> | <id>++ | <id>--
```

##### Q5
Write a BNF description of the Boolean expressions of Java, including the three operators &&, ||, and ! and the relational expressions.

##### A 
```
<expr> -> <expr> || <term> | <term>
<term> -> <term> && <factor> | <factor>
<factor> -> <id> | !<factor> | (<expr>) | <relationalExpr>
<relationalExpr> -> <id> > <id> | <id> < <id> | <id> <= <id> | <id> >= <id> | <id> == <id> | <id> != <id>
```

##### Q5
![](https://cdn.discordapp.com/attachments/845561994022879264/902304169258524722/unknown.png)

![](https://cdn.discordapp.com/attachments/845561994022879264/902304550604668948/unknown.png)