
2025-07-29

Tags: [[C]] [[Programming]] [[Compilers]]
# Stringizing Operator (#)

The **#** operator in C is called the stringizing operator  and it allows us to convert an argument into a string literal, which causes the actual argument to be enclosed in double quotation marks by the preprocessor. For example given ```#define PRINT_STRING(x) printf(#x)```, and we could then call our macro by doing: ```PRINT_STRING(Hello!);``` and it is completely valid.

This operator is mainly used inside of macros

# Token Passing Operator (##)
this is called the token pasting operator and it allows for tokens to be concatenated together to form other tokens, often done in macros. Note this is also done in the preprocessor before the code is compiled, also in the following example ```printf("%d", x ## y)``` should likewise be valid code."

Ex:
```
#include <stdio.h>

// Macro definition using the Token-pasting operator
#define concat(a, b) a##b
int main(void) {
    int xy = 30;

    // Printing the concatenated value of x and y
    printf("%d", concat(x, y));
    return 0;
}
```


# References

