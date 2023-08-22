SRC_DIR := .
BUILD_DIR := ./build
INCLUDE := -I$(SRC_DIR) -I$(SRC_DIR)/../signal_processing/build
OBJ_DIR := $(BUILD_DIR)/obj
SRC_FILES := $(wildcard $(SRC_DIR)/*.c)
OBJ_FILES := $(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SRC_FILES))
SRC_FILES += $(SRC_DIR)/vad.cc
OBJ_FILES += $(OBJ_DIR)/vad.o
H_FILES_SRC := $(wildcard $(SRC_DIR)/include/*.h)
H_FILES := $(patsubst $(SRC_DIR)/include/%.h, $(BUILD_DIR)/%.h, $(H_FILES_SRC))
LIB_FILE := $(BUILD_DIR)/vad.lib

all: $(BUILD_DIR) $(OBJ_DIR) $(LIB_FILE) $(H_FILES)

$(BUILD_DIR):
	mkdir -p $@
$(OBJ_DIR):
	mkdir -p $@

$(LIB_FILE): $(OBJ_FILES)
	ar rcs $@ $^

$(OBJ_DIR)/vad.o: $(SRC_DIR)/vad.cc
	g++ $(CXXFLAGS) $(INCLUDE) -c -o $@ $<

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c
	gcc $(CFLAGS) $(INCLUDE) -c -o $@ $<

$(BUILD_DIR)/%.h: $(SRC_DIR)/include/%.h
	cp $< $@
	sed -i -e 's@#include "include/@#include "@g' $@

clean:
	rm -rf $(BUILD_DIR)
