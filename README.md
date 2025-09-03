# NORMALIZATION PROBLEM

### OVERVIEW

  A function that normalizes the values on a given array. It creates a random 5x5 array and uses the formula to find its normal value. The values are saved as an .npy file.
  
### CODE

First, import the numpy library to our code.

    import numpy as np

Using the `.random.raindint()` function from numpy, create 5x5 2-dimensional array with random integers ranging from 1 to 100.

    X = np.random.randint(1,100, size = (5,5))
X
    
> [[56  6 12  8 15]\
   [27 51 20 14 50]\
   [ 8 45 39 86 91]\
   [69 31 45 39 49]\
   [20 90 37 81 89]]



Get the mean and the standard deviation from the array by using the `.meang()` and `.std()` function respectively.

    m = X.mean()
    s = X.std()
m
> 43.12

s
> 27.46243980421259

Create a new array using numpy to use it as a placeholder for the new normalized values.

    N = np.array(())

Create a for loop reading every row of the `X` array as its index `i`. Create another for loop within this for loop to read every element of index `i`. This reads every element of a 2 dimensional array in order. Using the formula for normalization, use the variables `j`, `m`, and `s` as the original value, mean, and standard deviation and substitute it to the formula:

<img width="103" height="52" alt="image" src="https://github.com/user-attachments/assets/e6c095a9-8383-4d92-bf7c-2f63381e2fcc" />


    for i in X:
        for j in i:
            z = (j - m) / s
            N = np.append(N,z)

N
> [ 0.46900421 -1.35166432 -1.1331841  -1.27883758 -1.02394398 -0.58698354
  0.28693736 -0.84187713 -1.06035735  0.25052399 -1.27883758  0.06845714
 -0.15002309  1.56140533  1.74347219  0.94237803 -0.44133005  0.06845714
 -0.15002309  0.21411062 -0.84187713  1.70705882 -0.22284983  1.37933848
  1.67064545]

Finally, resize the N array into a 5x5 format using `.resize()` and save the `N` array as X_normalized.npy.

    N.resize(5,5)
    np.save('X_normalized', N)

FULL CODE

    import numpy as np
    
    X = np.random.randint(1,100, size = (5,5))

    m = X.mean()
    s = X.std()
    
    N = np.array(())

    for i in X:
    for j in i:
        z = (j - m) / s
        N = np.append(N,z)

    N.resize(5,5)
    np.save('X_normalized', N)

### OUTPUT

    data1 = np.load('X_normalized.npy')
    print(data1)

>[[ 0.46900421 -1.35166432 -1.1331841  -1.27883758 -1.02394398]\
 [-0.58698354  0.28693736 -0.84187713 -1.06035735  0.25052399]\
 [-1.27883758  0.06845714 -0.15002309  1.56140533  1.74347219]\
 [ 0.94237803 -0.44133005  0.06845714 -0.15002309  0.21411062]\
 [-0.84187713  1.70705882 -0.22284983  1.37933848  1.67064545]]


# DIVISIBLE BY 3 PROBLEM

### OVERVIEW

A function that determines all the elements that are divisible by 3 on a 2 dimensional array. The values are saved as an .npy file

### CODE

First, import the numpy library into the code.

    import numpy as np

Create a numpy integer array as arr.

    arr = np.array((),dtype = int)

Using a for loop with its range from 1 to 101, calculate the squares of the first 100 integers by multiplying its index `i` by itself once. Using `.append()` store each value to the `arr` array in order.
    
    for i in range(1,101):
        arr = np.append(arr,i*i)
arr
> [    1     4     9    16    25    36    49    64    81   100   121   144
   169   196   225   256   289   324   361   400   441   484   529   576
   625   676   729   784   841   900   961  1024  1089  1156  1225  1296
  1369  1444  1521  1600  1681  1764  1849  1936  2025  2116  2209  2304
  2401  2500  2601  2704  2809  2916  3025  3136  3249  3364  3481  3600
  3721  3844  3969  4096  4225  4356  4489  4624  4761  4900  5041  5184
  5329  5476  5625  5776  5929  6084  6241  6400  6561  6724  6889  7056
  7225  7396  7569  7744  7921  8100  8281  8464  8649  8836  9025  9216
  9409  9604  9801 10000]

Resize array `arr` into a 10x10 array using `.resize()`

    arr.resize(10,10)
  > [[    1     4     9    16    25    36    49    64    81   100]\
   [  121   144   169   196   225   256   289   324   361   400]\
   [  441   484   529   576   625   676   729   784   841   900]\
   [  961  1024  1089  1156  1225  1296  1369  1444  1521  1600]\
   [ 1681  1764  1849  1936  2025  2116  2209  2304  2401  2500]\
   [ 2601  2704  2809  2916  3025  3136  3249  3364  3481  3600]\
   [ 3721  3844  3969  4096  4225  4356  4489  4624  4761  4900]\
   [ 5041  5184  5329  5476  5625  5776  5929  6084  6241  6400]\
   [ 6561  6724  6889  7056  7225  7396  7569  7744  7921  8100]\
   [ 8281  8464  8649  8836  9025  9216  9409  9604  9801 10000]]

Create a numpy integer array `d3` as a place holder for the elements on `arr` that are divisible by 3

    d3 = np.array((),dtype = int)

Create a for loop with the first dimension of `arr` as its element `i`. Create another for loop within it to access each element of the array denoted as `j`. Inside it, create an if statement where if the remainder of the element divided by 3 is zero, it will be saved to array `d3`. 


    for i in arr:
        for j in i:
            if j % 3 == 0:
                d3 = np.append(d3,int(j))

Finally, save the array `d3` on a .pny file named "div_by_3"

    np.save('div_by_3', d3)


FULL CODE

    import numpy as np

    arr = np.array((),dtype = int)

    for i in range(1,101):
      arr = np.append(arr,i*i)

    arr.resize(10,10)

    d3 = np.array((),dtype = int)

    for i in arr:
        for j in i:
            if j % 3 == 0:
                d3 = np.append(d3,int(j))
    
    np.save('div_by_3', d3)


### OUTPUT
    
    data2 = np.load('div_by_3.npy')
    print(data2)

> [   9   36   81  144  225  324  441  576  729  900 1089 1296 1521 1764
 2025 2304 2601 2916 3249 3600 3969 4356 4761 5184 5625 6084 6561 7056
 7569 8100 8649 9216 9801]
