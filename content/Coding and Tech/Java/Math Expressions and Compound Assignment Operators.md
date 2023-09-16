## Mathematical Operators:  
- Addition – `+`
- Subtraction – `-`
- Multiplication – `*`
- Division – `\`
- Modulus/Remainder – `%`  

## Examples:
```java
int a = 4 + 8;    // a = 12
double b = 5.6 - 1.5;    // b = 4.1
int c = 3 * 8;	// c = 24
double d = 15.0 / 3.0;   // d = 5.0
int e = 14 % 5;    // e = 4
```

## Integer vs floating point division
- When division occurs between two integers, the result is an integer and the fractional part of the result is truncated.
- On the other hand, when it occurs between two floating point numbers, nothing is truncated.
```java
int x, y = 14, z = 5
	x = y / z;         // x = 2     decimal portion is truncated
	int m = -13 / 3    //  m = -4

double r, s = 4.5, t = 2.0;
	r = s/t;      // r = 2.25
	double g = 14.0 / 5.0        //  g = 2.8
```

## Operator Precedence
- 1st:	`()`
- 2nd: `*  /  %`
- 3rd: `+  -`
## Mixed Mode Arithmetic and Casting Types
-  Data of different types will cast (change type) to the more inclusive type.   
- This can happen explicitly or implicitly.
Casting from int to double (implicit casting):
```java
double d = 3.3 + 2;    
// before addition occurs expression is changed to 3.3 + 2.0  then 5.3
double e  =  5 - 2.2;     // becomes 5.0 - 2.2    then becomes 2.8
double f  = 22.0 * 4;   //  becomes  22.0 * 4.0    or  88.0
double g = 15 / 4.5;    // becomes 15.0 / 4.5   or 1.5
double h = 2.8 % 1;    // becomes  2.8 % 1.0   or  0.8
```
Explicit casting:
```java
double mean;     
int finalMark;
finalMark = (int) mean;
```
## Compound Operators
- Things like `+=`, `-=`, `*=`, `--`, and `++` also work. 
## Rounding
- To round floating point numbers, use `(int)(n+0.5)` for positive and vice versa for negative. 