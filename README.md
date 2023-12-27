# Makefile_Tutorials
Makefile related tutorials

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


