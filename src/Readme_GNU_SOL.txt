Steps to create a shared object library for Epanet on Linux
===========================================================

1. Create a directory named Epanet_lib and copy the Epanet source files to it.

2. Uncomment the "#define SOL" line in epanet.c, and comment out the defines
   for DLL and CLE.

3. Create a shell script named "createlib" that contains the following lines:

#!/bin/sh
# Creates the epanet2 shared library
gcc -fPIC -c epanet.c hash.c hydraul.c inpfile.c input1.c input2.c input3.c \
mempool.c output.c quality.c report.c rules.c smatrix.c
ld -shared -soname libepanet.so.2 -o libepanet.so.2.11 -lc -lm epanet.o \
hash.o hydraul.o inpfile.o input1.o input2.o input3.o \
mempool.o output.o quality.o report.o rules.o smatrix.o
/sbin/ldconfig -v -n .
ln -sf libepanet.so.2 libepanet.so

4. Run the script to create the epanet shared object library that will consist
   of the files libepanet.so, libepanet.so.2, and libepanet.so.2.11.

5. Follow these steps when developing applications that use the EPANET Toolkit
   functions contained in the library:

   a. Copy the three library files to the directory where the application's
      source files reside.

   b. Update the environment variable LD_LIBRARY_PATH to include the directory
      by using the command:

      export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH

   c. Remember to add the switch "-lepanet" to the command line or to the
      makefile used to build the application.