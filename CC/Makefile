NAME  = name

CC    = clang++
OPTS  = -O0
DFLGS = -MP -MD
FLGS  = -Wall -Wextra -pedantic $(DFLGS)

SRC   = ./Source
OUT   = ./Output
BIN   = $(OUT)/$(name).exe

DIRS  = $(SRC)
SRCS  = $(foreach D,$(DIRS),$(wildcard $(D)/*.cc))
OBJS  = $(patsubst $(SRC)/%.cc,$(OUT)/%.o,$(SRCS))
DEPS  = $(patsubst $(SRC)/%cc,%.d,$(SRCS))

all: $(BIN)

run: $(BIN)
	$(BIN)

$(BIN): $(OBJS)
	$(CC) $^ -o $@ 

$(OUT)/%.o: $(SRC)/%.cc
	$(CC) -c $^ -o $@ $(CFLAGS)

clean:
	rm -rf $(OUT)/*

diff:
	@git status
	@git diff --stat

.PHONY: all clean diff

