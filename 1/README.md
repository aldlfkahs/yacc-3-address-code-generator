# 20141440 Compiler Project 1

## Main Idea of Your Solution
I stored the tokens by character pointer type and print them by printf("%s")
So, I made str attribute of yylval (yylval.str) and defined it at yacc file by %union.
I stored it to $n varaibles by character pointer using strdup() which returns the pointer of address of string.

## Code Description
In Assignment.y file, for example,

%left '+' '-'
%left '(multiply)' '/'
%right 'UMINUS'
%token <str>DIGIT
%token <str>ID
%type <str>E

E : E '+' E { printf("t%d = %s + %s\n", n, $1, $3); sprintf(tmp, "t%d", n++); $$=strdup(tmp); }
  | DIGIT { $$=yylval.str; }
  | '-' E %prec UMINUS {...}
  ....

## Detailed Algorithm
Detailed algorithm is shown above as code. 
I stored DIGIT and ID value in yylval.str.
Next, I stored the register number by concatenating t and global variable n using sprintf().
I stored it temporal variable 'tmp' because there was an error when I store it right away to $$.
Thus, I made $$ point to the start address of 'tmp'.

## anything else...

