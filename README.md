# Performance-Bounds-for-Near-Field-Velocity-Estimation-With-Modular-Linear-Array
The code can be used to produce results in Figures 2, 3, and 4, of our paper "Performance Bounds for Near-Field Velocity Estimation With Modular Linear Array" published in IEEE WCL, 10.1109/LWC.2026.3683974 
## Which file does what?

| File name                         | Purpose                                                                                           |
|-----------------------------------|---------------------------------------------------------------------------------------------------|
|`Generate_MSE.m`                   | Generates new Monte Carlo results in the workspace and plots MSE/CRB.                             |
|`simulate_velocity_mle.m`          | Generates one noisy observation, runs the MLE, and returns squared errors and velocity estimates. |
|`loss_function_mod.m`              | Likelihood objective and gradient used by `fminunc`.                                              |
|`match_filter_mod.m`               | Constructs the noise-free echo for a candidate velocity.                                          |
|`velocity_vector_mod.m`            | Antenna velocity projections and Doppler vectors.                                                 |
|`array_response_mod.m`             | Near-field array response, including the original per-antenna amplitude.                          |
|`crb_velocity_ula.m`               | ULA CRBs, Eqs. (16)–(17).                                                                         |
|`crb_velocity_mla.m`               | Modular-array CRBs, Eqs. (14)–(15).                                                               |
|`Fig_2_WCL.m`                      | Array-gain curves; requires your original `dirich_sinc.m`.                                        |
|`Fig_3_WCL.m`                      | Loads saved MSE data and plots it against CRBs.                                                   |
|`Fig_4_WCL.m`                      | Evaluates CRBs for different array configurations without pathloss.                               |
|`MSE_1000.mat`                     | Mean-squared error.                                                                               |

## Running the code

To display existing results:
```matlab
Fig_3_WCL
Fig_4_WCL
```

To generate new Monte Carlo results:
```matlab
Generate_MSE
```

**The original save command remains commented out.** To save after the script finishes, use a new filename:
```matlab
save('MSE_new.mat')
```

To plot this new file later, change the load line in `Fig_3_WCL.m` from `MSE_1000.mat` to `MSE_new.mat`.

`Generate_MSE.m` retains the original 1000 trials per range and `parfor` loop. It requires Optimization Toolbox (`fminunc`) and Parallel Computing Toolbox (`parfor`, `DataQueue`). 
