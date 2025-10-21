Adam Berry
568 Data Science
# 1
*a:*  Entropy(Class)
$$Entropy=-(10/20)\log_2(10/20)-(10/20)\log_2(10/20) = 1$$
 
*b:* Entropy(Movie ID)
	Since the Movie ID tag servers as an ID it is perfectly distributed and entropy is equal to $\log_2{20} \approx 4.32$ 
*c:* Entropy (Format)
$$Entropy = -(12/20)\log_2(12/20)-(8/20)\log_2(8/20) \approx 0.971$$
*d:* Entropy (Movie Category)
$$Entropy = -(8/20)\log_2(8/20)-(4/20)\log_2(4/20)-(8/20)\log_2(8/20) \approx 1.522$$
*e:*
	Of the three the movie format has the lowest entropy
*f:*
	Of the three attributes, based on entropy, I intuitively want to pick the format since it will result in the most balanced tree.
# 2
*a:*

| Number of + Instances | Number of - Instances | # correct | # total |
| --------------------- | --------------------- | --------- | ------- |
| 4                     | 0                     | 4         | 4       |
| 0                     | 1                     | 5         | 5       |
| 0                     | 1                     | 6         | 6       |
| 0                     | 1                     | 7         | 7       |
| 3                     | 0                     | 10        | 10      |
| 0                     | 5                     | 15        | 15      |
Using the pessimistic Approach:
$$err_{gen}(fig \space 1.)= 0+2*\frac{5}{15}=\frac{2}{3}$$
Optimistic Approach = $err_{gen}(fig \space 1.)= 0$ 
*b:*

| A   | B   | C   | D   | Number of + instances | Number of - Instances | # correct | # total |
| --- | --- | --- | --- | --------------------- | --------------------- | --------- | ------- |
| 0   | 0   | 0   | 1   | 4                     | 0                     | 0         | 4       |
| 0   | 0   | 1   | 1   | 3                     | 0                     | 0         | 7       |
| 0   | 1   | 0   | 0   | 0                     | 1                     | 1         | 8       |
| 0   | 1   | 1   | 0   | 0                     | 2                     | 3         | 10      |
| 1   | 0   | 0   | 0   | 2                     | 0                     | 5         | 12      |
| 1   | 0   | 0   | 1   | 3                     | 0                     | 8         | 15      |

Error rate is $8/15 \approx .5333$ 

*c:*
	I calculated that on the training set the model had a 0% error rate, yet on the test set the error rate was 53%. Furthermore the model had a high generalization error during training. All of this leads me to believe that this model was highly over fitted to the training data leading to the poor results, we ended up with a relatively complex model that also performs poorly. This is a great example case of what we talked about in class where letting models run too long can destroy model quality.