T = Assignment

all: $T

$T.tab.c:  $T.y
	bison -d $?
lex.yy.c: $T.l
	lex $?

$T: $T.tab.c lex.yy.c
	gcc -g  -o$@ $^

clean:
	rm -f $T.tab.[ch] lex.yy.c $T

zip: $T.l $T.y README.md
	zip submission.zip $^
