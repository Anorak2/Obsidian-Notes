
2025-05-13

Tags: [[Reverse Engineering]]
# Basic Anti-reversing Techniques
This is done to confuse disassembly tools, detect debuggers, and to make static analysis harder. We only focus on two techniques at the start, Packers and Obfuscators.

**Control Flow**
There are a number of different types: 
- Jumps with the same target
- jumps with constant conditions
- Impossible disassembly: this could be unreachable code but if that code was to be reached it creates an infinite loop. In practice this just gets jumped right over though.

### Packers
These are programs that take one executable and convert it to another packed executable; this can involve compressing, encryption, or other transformations. Packed malware for example needs to be unpacked before it can be statically analyzed, and it can help malware hide from antiviruses, make analysis harder, and reduce the binary size.
![[Pasted image 20250513224501.png]]
To detected a packed binary it may have very few or very strange sections, there also may be a packer indicator like UPX in the ```strings``` output. It can be difficult to unpack a program and it may need to be bespoke, if we know the packer algorithm then there may be an unpacking algorithm though.

**UPX**
UPX is a simple but popular open source packer.
Usage:
- Compile; gcc -o hello.orig hello.c
- Pack the binary; upx -o hello.pack hello.orig

when compared on a hello world program the file size went from 880k to 347k.

# References

