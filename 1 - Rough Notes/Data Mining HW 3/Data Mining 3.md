# 1.
#### 1.a:  
- True
#### 1.b: 
- C, decreases, the margin allowed decreases as C increases since we are choosing to penalize errors more. This is why, as mentioned, if we set C to infinity we get back to the hard margin variation.
# 2.
### 2.1
![[Pasted image 20251110224533.png]]
$w_{11} = 1, w_{12} = 0, b_1 =-3$

### 2.2
![[Pasted image 20251110225658.png]]

$w_{21} = -1, w_{22} = -.5, b_2 =3$

### 2.3
![[Pasted image 20251110231357.png]]
$w_{31} = 1, w_{32} = 1, b_3 =-1.5$
# 3
#### 3.1: 
- First Iteration: 
	- Assign values:
	- Centroid 1 (0.0)={0.1}
	- Centroid 2 (0.25)={0.2, 0.4}
	- Centroid 3 (0.6)={0.5, 0.6, 0.8, 0.9}
	
- Second Iteration
	- Compute New centroid values
	- C1 = 0.1,   C2 = 0.3,   C3 = 0.7

	- Assign values:
	- Centroid 1 (0.1) = {0.1, 0.2}          // Since I evaluated C1 first I assigned 0.2 here
	- Centroid 2 (0.3) = {0.4, 0.5}     // Same for 0.5
	- Centroid 3 (0.7) = {0.6, 0.8, 0.9}

- Third Iteration (Final)
	- Compute new centroid values
	- C1 = .15,  C2 = .45,  C3 = .77

	- Assign Values:
	- Centroid 1 (0.15) = {0.1, 0.2}
	- Centroid 2 (0.45) = {0.4, 0.5, 0.6}
	- Centroid 3 (0.77) = {0.8, 0.9}
#### 3.2
break it down into  component clusters
- C1: $(0.1-.15)^2 + (0.2-.15)^2 = 0.005$
- C2: $(0.4-.45)^2 +  (0.5-.45)^2 + (0.6-.45)^2=0.0275$
- C3: $(0.8 - .77)^2 +  (0.9-.77)^2=0.0178$ 

Recombine for total error:
SSE $= 0.005 + 0.0275 + 0.0178 = 0.0503$

#### 3.3

- $C_A$ (0.10) = {0.10, 0.20, 0.40, 0.50} // putting .5 here since I evaluated it first
- $C_B$ (0.90) = {0.60, 0.80, 0.90}

- Compute SSE
- $SSE(C_A$) = $(0.10-.10)^2 + (0.20-.10)^2 + (0.40-.10)^2 + (0.50-.10)^2=.26$
- $SSE(C_B)$ = $(0.60-.90)^2 + (0.80-.90)^2 + (0.90-.90)^2=.1$

- Split $C_A$ into $C_C \space (0.10)=\{0.1, 0.2\}$ and $C_D \space (0.5) = \{0.4, 0.5\}$

Compute Total SSE:
SSE = 0.1   +    (0.1-0.1)^2 + (0.2-0.1)^2    +   (0.4 - 0.5)^2 + (0.5 - 0.5^2)
SSE = 0.37

#### 3.4
On this dataset K-means clustering produced a significantly lower sum of squared error and I feel very comfortable saying it beat the bisecting k-means on this dataset. 
