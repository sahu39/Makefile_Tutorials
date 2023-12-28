MODULE_NAME = mod4

TARGET_DIR = ../../libs
TARGET_NAME = test_mod4.cpp
TARGET_BIN = test_mod4
TARGET = $(TARGET_DIR)/lib$(MODULE_NAME).a

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o

LIB_DIR = ../../libs
CFLAGS = -Wall -Werror
LDFLAGS = -L$(LIB_DIR) -l$(MODULE_NAME)

$(TARGET) : $(OBJ1)
	#g++ $< -o $@ $(LDFLAGS)
	ar rcs $@ $<
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

test:
	g++ $(TARGET_NAME) -o $(TARGET_BIN) $(LDFLAGS)
clean:
	rm -rf $(OBJ1) $(TARGET) 
