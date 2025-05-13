CC = gcc
FLEX = flex
BISON = bison
CFLAGS = -Wall -g

OBJS = main.o ast.o tabela.o lex.yy.o parser.tab.o

all: compilador

compilador: $(OBJS)
	$(CC) $(CFLAGS) -o $@ $(OBJS)

lex.yy.c: lex.l parser.tab.h
	$(FLEX) $<

parser.tab.c parser.tab.h: parser.y
	$(BISON) -d $<

main.o: main.c tabela.h
	$(CC) $(CFLAGS) -c $<

ast.o: ast.c ast.h tipos.h
	$(CC) $(CFLAGS) -c $<

tabela.o: tabela.c tabela.h tipos.h
	$(CC) $(CFLAGS) -c $<

lex.yy.o: lex.yy.c parser.tab.h
	$(CC) $(CFLAGS) -c $<

parser.tab.o: parser.tab.c parser.tab.h ast.h tabela.h tipos.h
	$(CC) $(CFLAGS) -c $<

clean:
	rm -f compilador $(OBJS) lex.yy.c parser.tab.c parser.tab.h

.PHONY: all clean