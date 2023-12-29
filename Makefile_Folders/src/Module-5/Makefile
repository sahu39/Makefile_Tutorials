MODULE_NAME = mod5

TARGET_DIR = ../../bins
TARGET_NAME = mod5_bin
TARGET = $(TARGET_DIR)/$(TARGET_NAME)

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o

LIBS_PATH = ../../libs
LDFLAGS = -L$(LIBS_PATH) -lmod2 -lmod4

INC_PATH = ../../shared_headers
CFLAGS = -Wall -Werror -I$(INC_PATH)

$(TARGET) : $(OBJ1)
	g++ $< -o $@ $(LDFLAGS)
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJ1) $(TARGET) 
