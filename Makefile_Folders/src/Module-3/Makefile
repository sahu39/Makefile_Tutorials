MODULE_NAME = mod3

TARGET_DIR = ../../bins
TARGET_NAME = mod3_bin
TARGET = $(TARGET_DIR)/$(TARGET_NAME)

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o
LIBS_PATH = ../../libs


CFLAGS = -Wall -Werror
LDFLAGS = -L$(LIBS_PATH) -lmod2

$(TARGET) : $(OBJ1)
	g++ $< -o $@ $(LDFLAGS)
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJ1) $(TARGET) 
