# FastGWR


Paper: [FastGWR](https://www.tandfonline.com/doi/full/10.1080/13658816.2018.1521523)

```
Li,Z., Fotheringham,A.S., Li,W., Oshan,T. (2018) Fast Geographically Weighted Regression (FastGWR): 
A Scalable Algorithm to Investigate Spatial Process Heterogeneity in Millions of Observations.
International Journal of Geographic Information Science. doi: 10.1080/13658816.2018.1521523
```

Fast computations developed in FastGWR have been integrated into  [`mgwr`](https://github.com/pysal/mgwr) python pacakge.

If you would like to use FastGWR directly (such as under HPC env), please read following instructions:

Install dependencies:

```
1. Install any MPI implementation
    OpenMPI: https://www.open-mpi.org
    Microsoft MPI: https://docs.microsoft.com/en-us/message-passing-interface/microsoft-mpi

2. Install `mpi4py` package
```

Example call to FastGWR which can be called on desktop or HPC:

```
mpiexec -np 4 python fastgwr-mpi.py -data input.csv -out results.csv -a -bw 1000
```

```
where:
-np 4: using 4 processors.
-data input.csv: input data matrix.
-out results.csv: output GWR results matrix including local parameter estimates, standard errors and local diagnostics.
-a (or --adaptive): Adaptive Bisquare kernel.
-f (or --fixed): Fixed Gaussian kernel.
-c (or --constant): Adding constant.
-bw 1000: Pre-defined bandwidth parameter. If missing, it will (golden-section) search for the optimal bandwidth and use that to fit GWR model.
-minbw 45: Lower bound in golden-section search.
```

The input needs to be prepared in this order:

| X-coord | Y-coord | y | X1 | X2 | ...| Xk |
|:-------:|:-------:|:-:|:--:|:--:|:--:|:--:|


```
where:
X-coord: X coordinate of the location point
Y-coord: Y coordinate of the location point
y: dependent variable
X1...Xk: independent variables
```
