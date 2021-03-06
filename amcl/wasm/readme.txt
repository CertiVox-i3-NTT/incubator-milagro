
AMCL in Webassembly 

See https://webassembly.org/getting-started/developers-guide/


The AMCL library already has a Javascript version, but can also run up 
to 10 times faster in a browser that supports Webassembly. And thats
most of the popular browsers in use today.*

The C, C++ or Rust version of the AMCL library can be compiled to a 
bitcode that runs directly in the browser, by-passing Javascript 
entirely. 

As of now only the 32-bit C version has been tested.

To install the Emscripten C/C++ compiler follow the instructions
above. Then copy the AMCL C code into a new directory, along with
the config.py file from this directory. In the new directory execute

python3 config.py

Then select options 1, 3, 7, 18, 20, 25, 26 and 27, which are fixed for 
the example programs.

Build the test programs with

emcc -O2 benchtest_all.c amcl.a -s WASM=1 -o benchtest_all.html

and

emcc -O2 testall.c amcl.a -s WASM=1 -o testall.html

Then run a browser (as described in the link above) and load the HTML file

Wait for the benchtest_all program to complete (which will take a while).

*Firefox, Safari, Edge, Chrome
