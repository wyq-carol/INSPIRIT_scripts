# PriorStarPU
`INSPIRIT/`: StarPU integrated with INSPIRIT  
`INSPIRIT_scripts/`: Scripts used to collect performance data  
`INSPIRIT_plots/`: Scripts used to draw performance plots
## Compile StarPU
We compile StarPU through `./configure --disable-fxt --enable-blas-lib=mkl --with-mkl-ldflags="-lmkl_intel_lp64 -lmkl_sequential -lmkl_core" && make`.

## Get Results
1. Generate DAG by analyzing trace

We first compile starpu with fxt enabled through `./configure --enable-blas-lib=mkl --with-mkl-ldflags="-lmkl_intel_lp64 -lmkl_sequential -lmkl_core" && make`. Then we can generate DAGs under `1_gen_trace_dag/cholesky/dag` in defined format.
```
./gen_trace_dag {task_name} {task_path} {task_script}
eg. ./gen_trace_dag.sh "cholesky" "/root/starpu_trace_view/examples/cholesky" "cholesky_implicit"
```

2. Generate priors by analyzing DAG

```
./gen_trace_dag {task_name} {task_path} {task_script}
eg. ./gen_trace_dag.sh "cholesky" "/root/starpu_trace_view/examples/cholesky" "cholesky_implicit"
```

3. Run baseline and SOTA

```
python gen_dif_env.py
```

4. Run INSPIRIT

```
python cholesky_scaling.py
```
## Draw Plots
Simply place the appropriate data under each directory and run the corresponding command to get the pdf under the corresponding directory.
```
python xxx.py
```