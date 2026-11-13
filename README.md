# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```python
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Sre Vishnu Priyar L N
RegisterNumber: 26009605
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def QR_Decomposition(a):
    n,m=a.shape
    q=np.empty((n,m))
    u=np.empty((n,m))
    u[:,0]=a[:,0]
    q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,m):
        u[:,i]=a[:,i]
        for j in range(i):
            u[:,i]-=(a[:,i]@q[:,j]*q[:,j])
        q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    r=np.zeros((m,m))
    for i in range(m):
        for j in range(i,m):
            r[i,j]=a[:,j]@q[:,i]
    print("The Q Matrix is\n",q)
    print("The R Matrix is\n",r)
a = np.array(eval(input()))
QR_Decomposition(a)
```

## Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0d82988e-ea9f-4e37-8d13-d06a202e7079" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3af3926d-28ab-456e-b1f9-ab389fbb7208" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
