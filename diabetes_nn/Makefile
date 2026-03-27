CC      = gcc
CFLAGS  = -Wall -Wextra -O2 -std=c99
LDFLAGS = -lm

SRC     = src/main.c src/data.c src/nn.c
OBJ     = $(SRC:.c=.o)
TARGET  = diabetes_nn
PREDICT = predict

.PHONY: all clean run predict_run

all: $(TARGET) $(PREDICT)

$(TARGET): $(OBJ)
	$(CC) $(OBJ) -o $@ $(LDFLAGS)

$(PREDICT): src/predict.c src/data.o src/nn.o
	$(CC) $(CFLAGS) -Isrc src/predict.c src/data.o src/nn.o -o $@ $(LDFLAGS)

src/%.o: src/%.c
	$(CC) $(CFLAGS) -Isrc -c $< -o $@

run: all
	./$(TARGET)

predict_run: $(PREDICT)
	./$(PREDICT)

clean:
	rm -f src/*.o $(TARGET) $(PREDICT)