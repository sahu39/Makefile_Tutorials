INPUT = Mod1.c
OUTPUT = ../../bins/Mod1_bin
OBJ1 = ../../objs/Mod1.o
CFLAGS = -Wall -Werror

#1st dependeny from INPUT is $(<) for all dependency $(^)
#output for all dependency $(@)
#-Wall = warning
#-Werror = error enable
$(OUTPUT) : $(OBJ1)
	gcc $< -o $@ -lm
$(OBJ1) : $(INPUT)
	gcc $(CFLAGS) -c $< -o $@
