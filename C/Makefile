CC    = clang
OPTS  = -O0
DFLGS = -MP -MD
FLGS  = -Wall -Wextra -pedantic $(DFLGS)

SRC   = ./Source
OUT   = ./Output
BIN   = $(OUT)/main.exe

DIRS  = $(SRC)
SRCS  = $(foreach D,$(DIRS),$(wildcard $(D)/*.c))
OBJS  = $(patsubst $(SRC)/%.c,$(OUT)/%.o,$(SRCS))
DEPS  = $(patsubst $(SRC)/%c,%.d,$(SRCS))

all: $(BIN)

run: $(BIN)
	$(BIN)

$(BIN): $(OBJS)
	$(CC) $^ -o $@ 

$(OUT)/%.o: $(SRC)/%.c
	$(CC) -c $^ -o $@ $(CFLAGS)

clean:
	rm -rf $(BIN) $(OBJS) $(DEPS)

diff:
	@git status
	@git diff --stat

.PHONY: all clean diff

