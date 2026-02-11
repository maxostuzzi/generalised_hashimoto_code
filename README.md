# Generalised Hashimoto's Algorithm

This is the discrete optimisation script for computing the optimal parameters $\ell$ and $b_i$ from the paper.
We make use of the Cryptogaphic Estimator library, which can be obtained from https://github.com/Crypto-TII/CryptographicEstimators .

## Optimisation Script

The optimisation script `generalised_hashimoto.py` takes as inputs the integers $n,m,q,p$ which are the number of variables, number of equations, field size and number of blocks for an instance of the MQ problem.
Additionally, to reduce the search space, one can indicate by specifying the additional input `--tobeat` the bit complexity "to beat".
One can also specify the number of workers and whether one wants all the parameters with tied complexity to be printed.

For example:
`python3 generalised_hashimoto_2.py --n 860 --m 78 --q 16 --p 6 --tobeat 155 --all-ties --workers 10`

## Evaluating the complexity

We have included an additional python script which, on input the integers $n,m,q,p$ as above and additionally $k, \ell$ and $b_i$, returns the corresponding complexity. This should be used, for example, to verify that the parameter choices
- $(n, m, q, k, p, \ell, b_i) = (860, 78, 16, 6, 32, 14, [4, 4, 4, 4, 4, 4])$ for MAYO SLI
- $(n, m, q, k, p, \ell, b_i) = (840, 100, 7, 4, 59, 13 , [3, 7, 7, 7])$ for QR-UOV SLI
satisfy the constraints of the optimisation problem and yield the bit complexities claimed in the paper.

For example:
`python3 eval_complexity.py -n 860 -m 78 -q 16 -k 32 -l 14 -bs 4 4 4 4 4 4`
