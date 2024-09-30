java c
ECA 5307 Python Programming for Economists
Midterm Exam
1. (2 marks) Find the index of “c” in cars from the following text.
text = "Don't park your car next to the carousel with cars."
2. (2 marks) You have given two Python sets as follows.
set1 = {1,3,5,7,9}
set2 = {1,2,4,6,9}
(a) (1 mark) Find the intersection of two sets.
(b) (1 mark) Remove those elements from the first set.
3. (2 marks) You have given a Python list.
list1 = [7,5,3,3,9,6,7]
(a) (1 mark) Write a program to check whether value 7 is in the list.
(b) (1 mark) If it is present, replace the first occurrence with 99.
4. (2 marks) Create an array of odd rows and even columns from Q4 below.
import numpy as np
Q4 = np.reshape(np.arange(0,90,3),(5,-1))
5. You have given a 2-D array Q5 as follows.
import numpy as np
np.random.seed(1204)
Q5 = np.random.randint(1,20,size=(4,5))
(a) (1 mark) Print max from axis 0.
(b) (1 mark) Print mean from axis 1.
6. (2 marks) With Bob’s high school reunion fast approaching, he decides to get in shape and loses some weight. He records his weight every day for five weeks starting on a Monday.
import numpy as np
np.random.seed(1204)
dailywts = 100 + np.random.randn(35)*2
Given these daily weights (dailywts), build an array with his average weight per midweek.
Note that a midweek includes Tuesday, Wednesday, and Thursday.
Hint: dailywts[0] is his weight on Monday, dailywts[1] is his weight on Tuesday, and so on.
7. Many regression models assume homoskedasticity (i.e., constant variance of the error term), especially when calculating standard errors. So in the presence of heteroskedasticity, stan-dard errors will be incorrect. Heteroskedasticity-consistent (HC) standard errors — also called “heteroskedasticity-robust,” or sometimes just “robust” standard errors — are calcu-lated without assuming such homoskedasticity.
Specifically, the HC estimator takes the form. as follows.

This formula is also known as the sandwich form, i.e.,

where

In this question, you will calculate the robust standard errors by using some functions in np.linalg. The data generating process is as follows.
import numpy as np
np.random.seed(1024)
n = 400
w = np.random.randn(n,1)
e = n代 写ECA 5307 Python Programming for Economists Midterm ExamPython
代做程序编程语言p.random.randn(n,1)
y = 3 + 5*w + e
(a) (2 marks) Calculate the OLS estimates by using np.linalg.lstsq(X,y), where X is the independent variable and y is the dependent variable.
Hint: First, you need to create a column vector const which is n × 1, and all elements of const are 1. Second, create the independent variable X by combining the const and w horizontally. Last, np.linalg.lstsq(X,y) returns a tuple in which the first element is what you need.
(b) (2 marks) Calculate the residuals.
Hint: The residuals is equal to y − Xβˆ, where βˆ is the OLS estimates from the previous question. Also, note that the multiplication (i.e., Xβˆ) is defined as linear algebra and can be done by using the operator @.
(c) (2 marks) Calculate the square of residuals.
(d) (2 marks) Create a matrix where the diagonal is the the square of residuals and the rest is zero, i.e.,

where ˆuiis the residual for i = 1, 2, . . . , 400.
Hint: First, use np.ravel() or np.squeeze(), to convert the 2-dimensional squared residuals from the previous question to an 1-dimensional array. Second, use np.diag() to create the matrix.
If you fail to create U, don’t worry. Please use U = 0.986*np.eye(n) for the following questions.
(e) (2 marks) Calculate the Ham,
Ham = XT UX,
where X> is the transpose of X.
Hint: Transpose can be done by .T or np.transpose(). Also, the multiplication (i.e., XT × U × X) is defined as linear algebra and can be done by using the operator @.
(f) (2 marks) Calculate the Bread,
Bread = (XT X)−1.
Hint: Use np.linalg.inv() to calculate the inverse. Also, the multiplication (i.e., XT × X) is defined as linear algebra and can be done by using the operator @.
(g) (2 marks) Calculate the robust var-covariance matrix,

Hint: Note that the multiplication (i.e., Bread × Ham × Bread) is defined as linear algebra and can be done by using the operator @.
(h) (2 marks) Calculate the robust standard errors.
Hint: Apply np.sqrt(np.diag()) to vcov.
(i) (2 marks) Please use the following code to verify your answer
import statsmodels.api as sm
mod = sm.OLS(y,X)
res = mod.fit(cov_type= 'HC1')
print(res.summary())
Are they same? If not, which step makes the difference?



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
