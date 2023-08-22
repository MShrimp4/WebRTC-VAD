SRC_DIR := .
BUILD_DIR := ./build
OBJ_DIR := $(BUILD_DIR)/obj
SRC_FILES := $(wildcard $(SRC_DIR)/*.c)
H_FILES_SRC := $(wildcard $(SRC_DIR)/include/*.h)
H_FILES := $(patsubst $(SRC_DIR)/include/%.h, $(BUILD_DIR)/%.h, $(H_FILES_SRC))
H_FILES += $(BUILD_DIR)/dot_product_with_scale.h
OBJ_FILES := $(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SRC_FILES))
LIB_FILE := $(BUILD_DIR)/signal_processing_library.lib

all: $(BUILD_DIR) $(OBJ_DIR) $(LIB_FILE) $(H_FILES)

$(BUILD_DIR):
	mkdir -p $@
$(OBJ_DIR):
	mkdir -p $@

$(LIB_FILE): $(OBJ_FILES)
	ar rcs $@ $^

$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c
	gcc $(CFLAGS) -I$(SRC_DIR) -c -o $@ $<

$(BUILD_DIR)/dot_product_with_scale.h: $(SRC_DIR)/dot_product_with_scale.h
	cp $< $@

$(BUILD_DIR)/%.h: $(SRC_DIR)/include/%.h
	cp $< $@

clean:
	rm -rf $(BUILD_DIR)
