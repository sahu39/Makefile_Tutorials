MODULE_NAME = mod4

TARGET_DIR = ../../libs
TARGET_NAME = mod4_bin
TARGET = $(TARGET_DIR)/lib$(MODULE_NAME).a

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o

CFLAGS = -Wall -Werror
LDFLAGS =

$(TARGET) : $(OBJ1)
	#g++ $< -o $@ $(LDFLAGS)
	ar rcs $@ $<
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJ1) $(TARGET) 
