# FastGWR


Install dependencies:

```
1. Download OpenMPI from https://www.open-mpi.org
2. pip install mpi4py
```
Example call to FastGWR:

```
mpiexec -np 4 python FastGWR.py -data input.csv -out results.csv -a -bw 1000
```

```
where:
-i input.dat: input data matrix
-o output.dat: output GWR results matrix
-a: Adaptive Bisquare kernel
-f: Fixed Gaussian kernel
-bw 1000: Predefined bandwidth parameter. If missing, it will search for the optimal bandwidth and use that to fit GWR model.
-aicc: using AICc as the optimization criterion
```

The input needs to be prepared in this order:

| X-coord | Y-coord | y | X1 | X2 | ...| Xk |
|:-------:|:-------:|:-:|:--:|:--:|:--:|:--:|

