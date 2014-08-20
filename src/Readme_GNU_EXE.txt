INSTRUCTIONS FOR COMPILING THE COMMAND LINE VERSION OF EPANET
            USING THE GNU C/C++ COMPILER ON LINUX
=====================================================================

1. Open the file EPANET.C in a text editor and make sure the line
       #define CLE
   is not commented out while the lines
       #define DLL
       #define SOL
   are commented out.

2. Copy the file "Makefile" to the directory where the EPANET engine
   source code files are located.

3. Open a console shell and navigate to the EPANET engine source
   code directory.

4. Issue the command:

      make

   to create an executable named epanet2.

