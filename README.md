# Bounded Quadrant System: Error-bounded trajectory compression on the go
Implementation of the 2015/2016 papers:

1. *J. Liu, K. Zhao, P. Sommer, S. Shang, B. Kusy and R. Jurdak, "Bounded Quadrant System: Error-bounded trajectory compression on the go," 2015 IEEE 31st International Conference on Data Engineering, 2015, pp. 987-998, doi: 10.1109/ICDE.2015.7113350.*

1. *J. Liu et al., "A Novel Framework for Online Amnesic Trajectory Compression in Resource-Constrained Environments," in IEEE Transactions on Knowledge and Data Engineering, vol. 28, no. 11, pp. 2827-2841, 1 Nov. 2016, doi: 10.1109/TKDE.2016.2598171.*


## Usage
This program calculates the optimal approximating curve to the original curve.
The given approximating curve has a global minimized maxmimum distance to the original curve.
Suppose the original curve has N points.
The approximating curve has m + 2 points (or sometimes less than m + 2) and m is assigned by the user (m <= N - 2).
The time complexity is O(N^3) and the space complexity is O(N^2).

The function 'solution, dmax, status = curve_approximation(x, y, m)' has the following inputs and outputs:

     x: an array of size N, the x coordinates of the orignal curve
     y: an array of size N, the y coordinates of the orignal curve
     m: the maximum number of sampling points (not including the first and the last points of the original curve)

     solution: a list of point index characterizing the approximating curve (including the first and the last points of the original curve)
               For example, the returned 'solution' may be [0, 3, 4, 9] for m = 2 and N = 10, which means the approximating curve is formed by the 0th, 3rd, 4th, 9th points of the orignal curve.
     dmax: the minimized maximum distance
     max_id: the index of the furthest point of the original curve
     status:  some interim variables of the algorithm for debugging use
