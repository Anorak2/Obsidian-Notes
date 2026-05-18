
[[Theory of Computing]]
It's possible to generate all possible strings using a set of substitution rules known as a formal grammar. 

$S^* = \{ \lambda,aa, ab, ba, bb, aaaa, aaab, ...\}$ 


$$E \to \lambda \mid aO \mid bO$$
$$O \to aE \mid bE$$
lets construct $baaa$ using the formal grammar:
$$E \to bO \to baE \to baaO \to baaa\lambda \to baaaa$$


we can also do the more intuitive option
$$E \to \lambda \mid aaE \mid abE \mid baE \mid bbE$$
