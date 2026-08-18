
2026-02-06

Tags: [[Data Mining and Machine Learning]]
# Support Vector Machines (SVM)
SVM's are a rather simple but powerful machine, it more or less draws a line in between features and then uses that line to predict a class and that's it. The tricky part with an SVM is drawing a line that is good. This is a surprisingly hard problem, so we use a trick where the extreme points of each class are used as base points and we select an equidistant line. This way the extreme points can be said to be "supporting" the line, hence the name. This obviously is much more complicated in hyper-dimensional spaces but the math is fundamentally the same.

![[Pasted image 20260206205416.png]]

**Strengths:**
- deterministic
-  Effective in cases where number of features is greater than the number of samples.
- Uses a subset of training points in the decision function (called support vectors), so it is also memory efficient.
- Versatile: different Kernel functions can be specified for the decision function.
**Weaknesses:**
- overfitting is possible, especially when we have more features than samples
- which kernel we select has an enormous relation with the quality of output
## Practical
Scikit has methods for multiclass svm 
```Python
svm.LinearSVC - Linear Support Vector Classification
svm.NuSVC - Nu-Support Vector Classification
svm.SVC - C-Support Vector Classification
```
It can also handle Support Vector Regression
```Python
svm.NuSVR – Nu-Support Vector Regression
svm.LinearSVR - Linear Support Vector Regression
svm.SVR - Epsilon-Support Vector Regression
```

Usually classification is used for discrete classes while SVR is used for continuous classes, but regression can be used for discrete by just fitting it to a value.

The difference between `SVC` and `NUSVC` is the kernel, but they are often talked about as if they were the same entity. For example `LinearSVC` will always use straight lines in its divisions.  

# References

