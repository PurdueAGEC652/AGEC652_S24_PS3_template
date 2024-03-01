*AGEC 652 - Spring 2024*

*Department of Agricultural Economics, Purdue University*

*Instructor: Diego S. Cardoso*


# Problem set 3

**Due Mar. 20 at 8 PM**

**Instructions**: To submit your solution, please commit and push your solution files to your GitHub Education repository. Files must be named `ps3_qX.jl` (or `.py`), where X is the number of the question you are solving. 


### Question 1

This question is a continuation of question 3 from Problem Set 2. We will return to the problem of estimating linear regression coefficients using Ordinary Least Squares (OLS). To recall, we follow a simple linear regression model:

$$y_i = \beta_0 + \beta_1 x_i + \epsilon_i$$

where $y_i$ is the dependent variable, $x_i$ is the independent variable, $\beta_0$ is the intercept, $\beta_1$ is the slope, and $\epsilon_i$ is the error term for observation $i$.

Your task is to estimate the parameter vector $\beta = [\beta_0, \beta_1]$ of this linear regression using numerical optimization. Once again, your repository will contain the same starter code that generates synthetic data for your estimation. Please do not modify that code and only insert your solution below it. *(If you are using a language other than Julia, please generate synthetic data following the same steps and true values of $\beta$.)*

A. **Optimization approach**: Solve for $\beta$ as the solution to a numerical minimization problem. The steps below outline how to do it.
   1. Let $F(\beta) = \sum_{i=1}^N (y_i - \beta_0 - \beta_1 x_i)^2$ be the sum of squared residuals we want to minimize. Program a function that take a candidate value $\beta^{(k)}$ and the sum of squared residuals $F(\beta_k)$.
   2. Use an adequate optimization solver of your choice to estimate $\beta$ using your function from the previous step (i.e., find the minimizer of $F$).

B. **Plotting**. To investigate the properties of this problem, prepare two graphs:
   1. Holding $\beta_1$ at its true value, plot the sum of squared residuals on a grid of points around the true value of $\beta_0$. This is, plot $F(b_0, \beta_1)$ for $b_0 \in [\beta_0-1, \beta_0+1]$.
   2. Now work with the other coefficient: holding $\beta_0$ at its true value, plot the sum of squared residuals on a grid of points around the true value of $\beta_1$. This is, plot $F(\beta_0, b_1)$ for $b_0 \in [\beta_1-1, \beta_1+1]$.

C. **Discussion**. Examine the shape of both graphs from part B and discuss how they visually relate the solution approaches of estimating coefficients as a numerical minimization or as a nonlinear system of equations.



### Setting for Questions 2 and 3

Consider a company that makes sophisticated mechanical arms for the automotive assembly industry. The production function of this company follows a Constant Elasticity of Substitution form

$$q(h,s) = \left[\gamma h^\rho + (1-\gamma)s^\rho\right]^\frac{\nu}{\rho}$$

where $h$ is the level of hardware input, $s$ is the level of software input, $\gamma$ is a share parameter, $\nu$ is a return-to-scale parameter, and $\rho$ is a substitution parameter (i.e., $\rho = \frac{\sigma-1}{\sigma}$, where $\sigma$ is the elasticity of substitution).

This company is vertically integrated and produces their hardware and software inputs using specialized labor and capital. Hardware is produced based on a Cobb-Douglas technology

$$h(l_h, k_h) = \alpha_h l_h^{\beta_{lh}}k_h^{\beta_{kh}}$$

where $l_h$ is the level of hardware-specialized labor, $k_h$ the level of hardware-specialized capital, $\alpha_h$ is the total factor productivity parameter, and $\beta_{lh}$ and $\beta_{kh}$ the share parameters for labor and capital.

Similarly, software production is given by

$$s(l_s, k_s) = \alpha_s l_s^{\beta_{ls}}k_s^{\beta_{ks}}$$

where parameters are analogous to the hardware case.

The objective of this function is to maximize the profits of producing mechanical arms given its market price $p$ (in thousands of dollars) and input prices $w_{lh}, w_{kh}, w_{ls}, w_{ks}$.

For problems 2 and 3, assume parameters have the following values (labor and capital prices are in thousands of dollars)

| Parameter | Value |
| --------- | ----- |
| $α_h$     | 0.8   |
| $α_s$     | 1.7   |
| $β_{lh}$  | 0.4   |
| $β_{kh}$  | 0.6   |
| $β_{ls}$  | 0.8   |
| $β_{ks}$  | 0.1   |
| $γ$       | 0.5   |
| $ν$       | 0.8   |
| $ρ$       | 0.75  |
| $w_{lh}$  | 12.0  |
| $w_{kh}$  | 34.0  |
| $w_{ls}$  | 43.0  |
| $w_{ks}$  | 8.0   |


### Question 2

Following the setting described above, use an appropriate numerical optimization method to find the solution for the profit maximization problem given any value of price $p$. 


A. **Plotting.** Prepare 3 separate graphs with the horizontal axis representing a grid of prices $p$ from 50 (thousand) to 300 (thousand)
   1. Plot the supply level $q^\star(p)$ on the vertical axis.
   2. Plot the profit level $\pi^\star(p)$ on the vertical axis.
   3. Plot a graph overlaying four curves, one for each optimal input use $(l_h^\star(p), k_h^\star(p),l_s^\star(p), k_s^\star(p))$ on the vertical axis.


### Question 3

Due to a global shortage of semiconductors, this firm is constrained in the short-term in its capital use. At the given (exogenous) market price, suppliers cannot fulfill capital orders, so this firm cannot exceed 10 units of capital usage in hardware $k_h$ or software $k_s$.

A. **Plotting.** Taking into account this new constraint, prepare the same 3 separate graphs from Question 2 but now accounting for the capital constraint.

B. **Discussion.** Compare your results from questions 2 and 3 and answer:
   1. At what price do capital constraints start binding? 
   2. At a price of $p=250$ (thousand), how much does the company lose in profits because of the capital constraint?




