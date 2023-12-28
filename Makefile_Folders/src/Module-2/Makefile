MODULE_NAME = mod2
TEST_MODULE = test_mod2.cpp

TEST_BIN_DIR = ../../test_build
TARGET_DIR = ../../libs
#TARGET_NAME = mod2
TARGET = $(TARGET_DIR)/lib$(MODULE_NAME).so

OBJ_DIR = ../../objs
OBJ1 = $(OBJ_DIR)/$(MODULE_NAME).o

CFLAGS = -fPIC -Wall -Werror
LDFLAGS =

$(TARGET) : $(OBJ1)
	g++ -shared $< -o $@ $(LDFLAGS)
$(OBJ1) : $(MODULE_NAME).cpp
	g++ $(CFLAGS) -c $< -o $@

build_dir:
	mkdir -p $(TEST_BIN_DIR)
	
test:
	g++ $(TEST_MODULE) -o $(TEST_BIN_DIR)/test_mod2 -L$(TARGET_DIR) -l$(MODULE_NAME)

clean:
	rm -rf $(OBJ1) $(TARGET) $(TEST_BIN_DIR) 
	sudo rm -rf /usr/lib/lib$(MODULE_NAME).so
install:
	sudo cp $(TARGET) /usr/lib/
	cp *.h ../../shared_headers

