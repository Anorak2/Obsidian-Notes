
2025-01-27

Tags: [[Reverse Engineering]] [[Compilers]]
# Software Build Process and Build Errors
```c
gcc -E  --> Preprocessor, but don't compile
gcc -S  --> Compile but don't assemble
gcc -c  --> Preprocess, compile, and assemble, but don't link
```

you can add -DCORRECT in order to declare a variable from the command line while compiling.

we can also add -lm, the l adds a lib and the m is .so so -lm ab -> lib ab.so. It tells gcc to include the math library, and it will look for the library in the library path

gcc -c -fpic mul.c (creates a .o file with more information than usual), gcc -shared -o <.so> <.o>

**Preprocessor**
This is the front of the chain and it runs before the compiler does, and it outputs a preprocessed .i file. This handles lines that start with a hashtags, like includes and defines.

Handles files with a hashtag in front of them

**Compiler**
The compiler takes the .i file from before, compiles it, and then it turns out assembly code (which is a .s)

**Assembler**
The assembler takes the .s file and converts that file into object code (.o)

**Linker**
The linker resolves external references (Dependencies). When we include a file in say math.h that including only contains the headers, by that it is all of the functions and the function arguments. We do it this way because it allows for dynamic linking, which means we don't have to statically include the function in the binary which makes our binary longer.
# References

