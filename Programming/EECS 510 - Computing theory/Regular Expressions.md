
[[Theory of Computing]]
Strings ending with ab, (a+b)*ab
strings that begin and end with different symbols $a(a+b)*b + b(a+b)*a$
Strings of even length, $((a+b)(a+b))*$
Strings with an even number of as $(ab*a+b)$ 

Operators in precedence
1. Grouping
2. Kleene Star (like exponents)
3. Concatenation (like multiplication)
4. Union (like addition)

**Rules**
There are some rules such as
$$aa + ab = a(a+b)$$
$$b+ba=b(\lambda+b)$$
Ordering matters:
$$a(a+b) \not = (a+b)a$$
left means a followed by a/b, right means a/b followed by a
$a^3$ is shorthand for $aaa$ and is a regular expression

| Rule                       | Description                                 |
| -------------------------- | ------------------------------------------- |
| $r+s=s+r$                  | Union is commutative                        |
| $(r+s)+t=r+(s+t)$          | Union is associative                        |
| $r+r=r$                    | Union is idempotent                         |
| $r+\phi = r$               | Unions identity element is $\phi$           |
| $rs(t) = r(st)$            | Concatenation is associative                |
| $r\lambda = \lambda r = r$ | Concatenations identity element is $\theta$ |
| $r\phi = \phi r = \phi$    | Concatenations identity element is $\phi$   |
| $r(s+t)=rs+rt$             | Concatenation over union is distributive    |
**Character Classes**
Bracketed groups are called character classes and represent a set of acceptable characters
$[A-Za-z]:$ Represents any letter
$[A-Za-z]^+ == [A-Za-z][A-Za-z]^*$ have to pick one, followed by any 
$[aeiou]$ represents and single vowel character
$[0-9]$ any digit

What do we do when our language doesn't have an easily findable regex function?
Fortunately we can convert any finite auto

