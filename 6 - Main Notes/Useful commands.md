
2025-03-13

Tags: [[Reverse Engineering]] [[linux]]
# Useful commands
**file**
file [flags]  file_name/s
- File attempts to find the file type and shows some other basic information about the file
**strings**
strings -flags file_name/s
* Strings prints all sequences of printable characters in a file
* can use -n for imposing a minimum length, or -e for changing the encodings
**objdump**
objdump -flags file_name
- object dump exists to display information about object files where the flags controls what specifically is show
-  -D; this is the most useful and it decompiles everything 
- -s -j .section; D displays that section of the binary
**ldd** 
ldd -options file
- ldd is used to find the shared libraries (objects) required by each program
**gdb**
![[Pasted image 20250313234033.png]]

**grep**

**chmod**
- changes the permissions of a file, especially useful for +x and -x
**nm**
- Lists the symbols from object files

export LD_LIBRARY_PATH
echo $LD_LIBRARY_PATH
source ~/.bashrc

**generate ssh keypair -> send to keepassxc**
	`ssh-keygen -o -f keepassxc -C johndoe@example`
# References

