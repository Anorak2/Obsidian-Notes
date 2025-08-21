
2025-05-13

Tags: [[Reverse Engineering]]
# LD Preload
This is a way to do function hijacking since LD_PRELOAD allows users to provide their own definitions for dynamic symbols, and we can load these symbols before a library can load it's symbols.
```
#include <stdlib.h>

int strncmp(char *__s1,char *__s2,size_t __n){
	return 0;
}

double pow(double x, double y){
	if(y == 10.0){
		return 64.0;
	} else{
		return 1.0;
	}
}

int rand(){
	return 0;
}
```

**Steps:**
- Compile program as usual; ```gcc prog.c```
- Compile custom library file into a .so object file
	-```gcc -fPIC -shared -o lib.so lib.c```
* Use LD_PRELOAD to instruct the OS to link my .so file first
	-```LD_PRELOAD=./lib.so ./a.out```

```
#include <math.h>

double pow(double x,double y){
    double (*original_pow)(double, double);
    original_pow = dlysm(RTLD_NEXT, "pow");

    if (y == 10.0){
        y = 6.0;
    }

    return (*oringal_pow)(x,y);

}
```


# References

