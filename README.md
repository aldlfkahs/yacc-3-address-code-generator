# yacc-3-address-code-generator
The goal of this project is to make 3-address-code generator by implementing yacc as well as lex file. In lex file(.l file), I defined grammar by using regular expressions. After lex file tokenizing the input string, it passes token to yacc(.y file). In yacc file, you can see actual implemeting for 3-address-code generator. Typing 'make', you could get executable file 'Assignment'.


### Directory 1
In directory 1, I only considered four fundamental rules of arithmetics, unary minus and parentheses.


### Directory 2
In directory 2, I expanded what I implemented in directory 1. Now it also handles multi-dimension array and type.


#### *Detailed description is in each directory
