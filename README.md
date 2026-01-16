# Time-Invariant and Time-Varying MVAR Toolbox

This repository provides a Python toolbox for **simulating, estimating, and visualizing multivariate autoregressive (MVAR) processes**, including both **time-invariant (TiV)** and **time-varying (TV)** variants. It also includes a collection of **basis function generators** for modeling time-varying coefficients and tools for sliding-window analysis.

---

## Features

### 1. Simulation
- **TiV-MVAR simulation:** Generate data from a time-invariant MVAR model.  
  `TiV_MVAR_simulator(A, x0, t, noise=None)`  
- **TV-MVAR simulation:** Generate data with time-varying MVAR coefficients.  
  `TV_MVAR_simulator(A, t_seg_edges, x0, t, noise=None)`

### 2. Estimation
- **TiV-MVAR estimation:** Estimate MVAR coefficients from multivariate time series.  
  `TiV_MVAR_estimator(data, MaxLagOrder, Order_selection_criterion=None, Order_selection_print=False)`  
- **TV-MVAR estimation using sliding window:** Estimate time-varying MVAR coefficients over moving windows.  
  `TV_MVAR_estimator_sliding_window(data, time, MaxLagOrder, window_size, window_shift, t_ref_loc='mid', Order_selection_criterion=None, Order_selection_print=False)`  
- **TV-MVAR estimation using RLS (Recursive Least Squares):**  
  `TV_MVAR_estimator_RLS(data, time, LagOrder=3, A0=None, P0=None, lambda_=0.90)`  
- **TV-MVAR estimation using Kalman Filter:**  
  `TV_MVAR_estimator_KF(data, time, LagOrder, A0=None, P0=None, F=None, R=None, Q0=None, LAMBDA=None, smoothing=False)`  
- **TV-MVAR estimation using multiple basis expansion:**  
  `TV_MVAR_estimator_MultipleBasisExpansion(data, time, BasisLib, LagOrder)`

### 3. Order Selection
- **Sliding-window order selection for MVAR models:**  
  `Sliding_Window_Order_selection_func(data, MaxLagOrder, window_size, window_shift, Order_selection_criterion='aic', Order_selection_print=False)`

### 4. Basis Function Generators
- Polynomial bases: `basis_Legendre`, `basis_Chebyshev`  
- Walsh functions: `basis_Walsh`  
- Fourier bases: `basis_Fourier_Sin`, `basis_Fourier_Cos`  
- Wavelets: `basis_Wavelet_Morlet`, `basis_Wavelet_Ricker`

### 5. Visualization
- Plot time-varying matrices (MVAR coefficients, connectivity, etc.):  
  `plot_TV_matrix(A, t, pValues=None, shareAxes=None)`
