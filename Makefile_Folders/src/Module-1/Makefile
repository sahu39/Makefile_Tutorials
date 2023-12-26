INPUT = Mod1.c
OUTPUT = ../../bins/Mod1_bin
OBJ1 = ../../objs/Mod1.o
#1st dependeny from INPUT is $(<) for all dependency $(^)
#output for all dependency $(@)
$(OUTPUT) : $(OBJ1)
	gcc $< -o $@
$(OBJ1) : $(INPUT)
	gcc -c $< -o $@
