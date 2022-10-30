NAME=kplc
EXT=cc
CC=clang++

SRC=./Source
OUT=./Output
OBJ=$(OUT)/Objects
BIN=$(OUT)/$(NAME).exe

DIRS=.
INCS=$(foreach D,$(DIRS),$(SRC)/$(D))
SRCS=$(foreach D,$(INCS),$(wildcard $(D)/*.$(EXT)))
OBJS=$(patsubst $(SRC)/%.$(EXT),$(OBJ)/%.o,$(SRCS))

EFLGS=-std=c11 -O3 -g
WFLGS=-Werror -Wall -Wextra -pedantic
FLGS=$(EFLGS) $(WFLGS) $(foreach D,$(INCS),-I$(D))

all:$(BIN)

run:$(BIN)
	$(BIN)

$(BIN):$(OBJS)
	$(CC) $^ -o $@

$(OBJ)/%.o:$(SRC)/%.$(EXT)
	$(CC) -c $^ -o $@ $(FLGS)

clean:
	rm -rf $(OUT)/*
	mkdir $(OBJ)
	mkdir $(foreach D,$(DIRS),$(OBJ)/$(D))

diffs:
	@git status
	@git diff --stat

.PHONY:all clean diff

