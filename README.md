# Makefile_Tutorials
Makefile related tutorials
link:https://stackoverflow.com/questions/480764/linux-error-while-loading-shared-libraries-cannot-open-shared-object-file-no-s
Module-2 Makefile Running steps:
=====================================
1st:(Running make to create libraries and test binary)
----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2$ make
g++ -fPIC -Wall -Werror -c mod2.cpp -o ../../objs/mod2.o
g++ -shared ../../objs/mod2.o -o ../../libs/libmod2.so 

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2$ make build_dir 
mkdir -p ../../test_build

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2$ make test
g++ test_mod2.cpp -o ../../test_build/test_mod2 -L../../libs -lmod2

2nd:(Checking the Dynamic Library Path)
----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/libs$ ls
libmod2.so

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/libs$ pwd
/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/libs

3rd:(Setting Dynamic Library Path)
----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/test_build$ echo $LD_LIBRARY_PATH

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/test_build$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/libs/

4th:(Running the Binary)
-----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/test_build$ ./test_mod2 
.so implementation:fun2()



=================================



Module-3 Makefile Running steps:
=================================
1st:(Run the Makefile in Module-2)
====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-3$ make -C ../Module-2
make: Entering directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'
g++ -fPIC -Wall -Werror -c mod2.cpp -o ../../objs/mod2.o
g++ -shared ../../objs/mod2.o -o ../../libs/libmod2.so 
make: Leaving directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'

2nd:(Install the mod-2 library into /usr/lib/ folder)
====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-3$ make -C ../Module-2 install
make: Entering directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'
sudo cp ../../libs/libmod2.so /usr/lib/
cp *.h ../../shared_headers
make: Leaving directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'

3rd:(Run the Makefile for Module-3)
=====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-3$ make
g++ -Wall -Werror -I../../shared_headers -c mod3.cpp -o ../../objs/mod3.o
g++ ../../objs/mod3.o -o ../../bins/mod3_bin -L../../libs -lmod2

4th:(Run the binary for test):
================================
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-3$ ../../bins/mod3_bin 
.so implementation:fun2()

=====================================



Module-4 Makefile Running steps:
=================================
1st:(Running Make for module-4)
===
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ make
g++ -Wall -Werror -c mod4.cpp -o ../../objs/mod4.o
#g++ ../../objs/mod4.o -o ../../libs/libmod4.a 
ar rcs ../../libs/libmod4.a ../../objs/mod4.o

2nd:(Checking static library is created or not):
===
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ ls -l ../../libs/
total 4
-rw-rw-r-- 1 km km 2930 Dec 28 16:20 libmod4.a

Error while compiling test_mod4.cpp:
=================================
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ ls
Makefile  mod4.cpp  mod4.h  test_mod4.cpp

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ g++ test_mod4.cpp -o test_mod4
/tmp/ccWxsvI1.o: In function `main':
test_mod4.cpp:(.text+0x2d): undefined reference to `fun4()'
collect2: error: ld returned 1 exit status

Solution to resolve the error is link the library while compilation:
===================================================================
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ g++ test_mod4.cpp -o test_mod4 -L../../libs -lmod4

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ ls
Makefile  mod4.cpp  mod4.h  test_mod4  test_mod4.cpp

Run the test_mod4 binary:
==========================
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4$ ./test_mod4 
Testing Module-4
Inside fun4()

=================================




Module-5 Makefile Running steps:
================================
1st:(install the Module-2 library)
====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ make -C ../Module-2/ install
make: Entering directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'
sudo cp ../../libs/libmod2.so /usr/lib/
[sudo] password for km: 
cp *.h ../../shared_headers
make: Leaving directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-2'

2nd:(install the Module-4 library)
====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ make -C ../Module-4
make: Entering directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4'
make: '../../libs/libmod4.a' is up to date.
make: Leaving directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4'
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ make -C ../Module-4 install
make: Entering directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4'
cp mod4.h ../../shared_headers
make: Leaving directory '/home/km/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-4'

3rd:(Run the mod5_bin)
====
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ ls ../../shared_headers/
mod2.h  mod4.h

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ make
g++ -Wall -Werror -I../../shared_headers -c mod5.cpp -o ../../objs/mod5.o
g++ ../../objs/mod5.o -o ../../bins/mod5_bin -L../../libs -lmod2 -lmod4

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/Module-5$ ../../bins/mod5_bin 
Module-5 Tutorial
.so implementation:fun2()
Inside fun4()



================================

Note For Makefile:
===================


				Source Code(Sample.c)
					|
			compiler	| -c
		       -Wall -Werror	|
					|
				   object file
					|
			Linker		|  <---linker flags
					|    (-lm -lzmq -lcurl -lxyz)
					|
				   Executable

	gcc $(CFLAGS) -c $< -o $@
	gcc $< -o $@ $(LDFLAGS)	



How to define header outside and compile:
==========================================
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/MACRO$ gcc macro_eg.c
macro_eg.c: In function ‘main’:
macro_eg.c:5:16: error: ‘MY_MACRO’ undeclared (first use in this function)
  printf("%s\n",MY_MACRO);
                ^~~~~~~~
macro_eg.c:5:16: note: each undeclared identifier is reported only once for each function it appears in


km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/MACRO$ gcc -DMY_MACRO=\"Sunil\" macro_eg.c 

km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/MACRO$ ls
a.out  macro_eg.c


km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/MACRO$ ./a.out 
Sunil


=====================================================================


= vs :=
=======

=------------>Lazy Initialization
:=----------->Instant Intialization

Makefile:
-----------
  1 VAR1 = 10----->Lazy Initializtion
  2 VAR2 = 20
  3 
  4 VAR1 = $(VAR1) 1000
  5 
  6 default:
  7         echo $(VAR1)-------->Here when $(VAR1) is called the initializtion happens from here so lazy initializtion


op:
---
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ make
Makefile:4: *** Recursive variable 'VAR1' references itself (eventually).  Stop.



Makefile:
---------------
  1 VAR1 = 10
  2 VAR2 = 20
  3 
  4 VAR1 := $(VAR1) 1000------>Instant initilization of VAR1 
  5 
  6 default:
  7         echo $(VAR1)

op:
-----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ make
echo 10 1000
10 1000



=====================================================================

PHONY TARGET:
============
Makefile:(Without PHONY Target)
-----------
  1 VAR1 = 10
  2 VAR2 = 20
  3 
  4 VAR1 := $(VAR1) 1000
  5 
  6 default:
  7         echo $(VAR1)


km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ touch default
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ ls
default  Makefile

op:(As physical target 'default' is already exist we are getting below message when we are running make)
----
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ make
make: 'default' is up to date.



Makefile:(With PHONY Target)
---------
  1 VAR1 = 10
  2 VAR2 = 20
  3 
  4 VAR1 := $(VAR1) 1000
  5 
  6 default:
  7         echo $(VAR1)
  8 
  9 .PHONY: default

op:
---
km@KernelMasters:~/Desktop/Makefile_Tutorials/Makefile_Folders/src/eq_ceq$ make
echo 10 1000
10 1000
                    

======================================================================




