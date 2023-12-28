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

=================================






