MODULE_NAME = mod2

TARGET_DIR = ../../libs
TARGET_NAME = mod2
TARGET = $(TARGET_DIR)/lib$(TARGET_NAME).so

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o

CFLAGS = -fPIC -Wall -Werror
LDFLAGS =

$(TARGET) : $(OBJ1)
	g++ -shared $< -o $@ $(LDFLAGS)
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(OBJ1) $(TARGET) 
