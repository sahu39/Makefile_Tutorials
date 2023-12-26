INPUT = Mod1.c
OUTPUT = ../../bins/Mod1_bin
OBJ1 = ../../objs/Mod1.o

#1st dependeny from INPUT is $(<) for all dependency $(^)
#output for all dependency $(@)
#-Wall=warning

$(OUTPUT) : $(OBJ1)
	gcc $< -o $@ -lm
$(OBJ1) : $(INPUT)
	gcc -Wall -c $< -o $@
