##
## Makefile for elfsh
## 
## Started on  Sun Mar 10 01:19:24 2002 jfv
## Last update Sun Dec 15 01:55:59 2002 jfv
##

include ../../../config.h

SRC	= hash_read.c
CC	= gcc
RM	= rm -f 
VULN	= main.c

OBJ32	= $(SRC:.c=.32.o)
OBJ64	= $(SRC:.c=.64.o)
CFLAGS32  =$(shell eresi-config32 libelfsh --cflags)
LDFLAGS32 =$(shell eresi-config32 libelfsh --libs)
CFLAGS64  =$(shell eresi-config64 libelfsh --cflags)
LDFLAGS64 =$(shell eresi-config64 libelfsh --libs)
NAME32	= hash_reader32
NAME64	= hash_reader64

all: all32 all64

all32: $(OBJ32)
	$(CC) $(OBJ32) -o $(NAME32) $(LDFLAGS32) 
	$(CC) $(VULN) -o readme32

all64: $(OBJ64)
	$(CC) $(OBJ64) -o $(NAME64) $(LDFLAGS64) 
	$(CC) -m64 $(VULN) -o readme64

fclean: clean
	$(RM) $(NAME32) $(NAME64) readme*

clean:
	$(RM) $(OBJ32) $(OBJ64) *~

%.32.o:	%.c
	$(CC) -c $< -o $@ $(CFLAGS32) -g

%.64.o:	%.c
	$(CC) -c $< -o $@ $(CFLAGS64) -g
