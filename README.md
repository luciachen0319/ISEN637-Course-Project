This is the course project of ISEN637. In this project, we compare between the SDDP and Actor-Critic algorithms on the hydro-thermal scheduling example.

# How to run the code
## Install Required Packages
The scripts rely on several Julia packages (most notably `SDDP.jl` and `JuMP.jl`). You need to install these first.
1. Open your terminal or command prompt.
2. Type `julia` to open the Julia REPL.
3. Press `]` to enter the Pkg (Package Manager) mode.
4. Run the following command to install all dependencies found in your files:
```
add SDDP HiGHS JuMP CSV DataFrames Distributions Plots
```
5. Press `Backspace` to exit Pkg mode, and type `exit()` to close the REPL.

## Execute the Program
If you want to train and simulate a specific formulation, you can run the individual model scripts directly.

- For the Markov Chain approach:
```
julia sddp_mc.jl
```
- For the Time Series / Continuous Noise approach:
```
julia sddp_ts.jl
```
When you execute either of these files, the program will:
1. Call `read_data_sddp.jl` to load the baseline `hydro.csv`, `thermal.csv`, `demand.csv`, etc.
2. Build a standard SDDP policy graph focusing solely on operational decisions (`hydro`, `spill`, `thermal_gen`, `deficit`, `exchange`).
3. Train the model using `SDDP.train()`.
Run Monte Carlo forward simulations to test the trained policy.
4. Use `save_results_sddp.jl` to output the simulated operational results into the `output/simulation/` folder.