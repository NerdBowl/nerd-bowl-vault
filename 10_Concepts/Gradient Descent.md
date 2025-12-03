---
tags:
  - topic/optimization
  - topic/line-search
  - topic/machine-learning
  - topic/ai
aliases: []
status: good_enough
created: 2025-12-03 13:45
---
# Gradient Descent (Steepest Descent)
### Gradient Descent
This method of [[10_Concepts/Line Search Methods|line search]] chooses the direction in which the function decreases fastest.
- **Direction**: The steepest descent direction is the negative [[10_Concepts/Gradients|gradient]]: $p=-\nabla f(x)$.
- **Derivation ($\phi'$ Analysis)**:
    - We analyze the "slice" of function $f$ along a direction $p$ using the scalar function $\phi(\alpha) = f(x + \alpha p)$.
    - The rate of change of $f$ at $x$ along $p$ is the derivative $\phi'(0) = \nabla f(x)^\top p$.
    - By the Cauchy-Schwarz inequality, $\nabla f(x)^\top p \ge - \|\nabla f(x)\| \|p\|$.
    - Consequently, choosing $p = -\nabla f(x)$ attains this lower bound, yielding the steepest possible descent.
- **Limitations**: Gradient Descent often zigzags or overshoots the [[Minimizers|minimizer]], especially with fixed step lengths.

### Stochastic Gradient Descent
In machine learning problems, among others, the objective function is a sum of $m$ terms, making it computationally expensive to calculate the full gradient when $m$ is large. 

To minimize $f(x)=\frac{1}{m}\sum_{j=1}^m f_{j}(x)$:
- $x_{k+1}=x_{k}-\alpha_{k}\frac{1}{|\mathcal{B}_{k}|}\sum_{j\in\mathcal{B}_{k}}\nabla f_{j}(x_{k})$
- $\mathcal{B}_k \subseteq \{1, ..., m\}$

To ensure convergence and dampen noise, step lengths $\alpha_{k}$ must decay such that they satisfy the [[10_Concepts/Robbins-Monro conditions|Robbins-Monro conditions]]:
$$\sum_{k=1}^{\infty} \alpha_k = \infty \quad \text{and} \quad \sum_{k=1}^{\infty} \alpha_k^2 < \infty$$

#### Stochastic Optimization
Using gradient statistics, the noisy gradients calculated from mini-batches can be made more stable. The core mechanism for this is the Exponentially Weighted Moving Average.

##### EWMA (Exponentially Weighted Moving Average)
EWMA allows us to estimate the statistical properties (mean and variance) of the gradient without storing the entire history of previous steps.
- **Formula**: $z_{k} = \beta z_{k-1} + (1-\beta)y_{k}$
  Where $z_k$ is the running average, $y_k$ is the new observation (e.g., the current gradient), and $\beta \in [0, 1)$ is the decay rate.
- **Efficiency**: This provides a running average while only requiring one extra value ($z_{k-1}$) to be stored per parameter.
- **Bias Correction**: Since $z_0$ is initialized to 0, the average is biased towards zero during the initial steps. This is corrected by scaling the estimate: $\hat{z}_{k} = \frac{z_{k}}{1 - \beta^k}$
EWMA is the building block for sophisticated optimizers that utilize the "moments" of the gradient:
##### Momentum
This method applies EWMA to the gradient vector itself ($g_k$) to estimate the first moment (mean).
- **Estimate Formula**: $m_{k} = \beta_{1}m_{k-1} + (1-\beta_{1})g_{k}$
  Here, $m_k$ represents the accumulated direction of the gradient.
- **Parameter Update**: $x_{k+1} = x_k - \alpha m_k$
- **Mechanism**: By averaging the gradients over time, high-frequency noise caused by random mini-batch selection cancels out, while the consistent direction of the gradient accumulates. This acts as a low-pass filter, smoothing the optimization path and preventing the "zigzag" effect common in stochastic settings.
##### RMSProp
This method applies EWMA to the element-wise square of the gradient ($g_k \circ g_k$) to estimate the second moment (uncentered variance).
- **Estimate Formula**: $v_{k} = \beta_{2}v_{k-1} + (1-\beta_{2})(g_{k} \circ g_{k})$
  Here, $v_k$ represents the magnitude (variance) of the gradients for each parameter.
- **Parameter Update**: $x_{k+1} = x_k - \frac{\alpha}{\sqrt{v_k} + \epsilon} g_k$
- **Mechanism**: This estimate is used to normalize the step size:
    - If the variance $v_k$ is **high** (steep gradients/high uncertainty), the term $\frac{1}{\sqrt{v_k}}$ scales the step down to prevent instability.
    - If the variance $v_k$ is **low** (flat regions), the step size increases to accelerate progress.

##### ADAM (Adaptive Moment Estimation)
Adam is the modern default for stochastic minimization. It adapts the learning rate for each parameter based on estimates of the first and second moments of the gradients. It combines RMSprop and Momentum.

**Algorithm**
- **Initialize**: Step length $\alpha$, decay rates $\beta_1, \beta_2 \in [0, 1)$, $\epsilon > 0$, $x_0$, and moments $m_0 = 0, v_0 = 0$.
- **Iterate:**
	- Select mini-batch $\mathcal{B}_{k}$, and compute gradient $g_{k}$.
	- Update First Moment (estimate of true gradient): $m_{k} \leftarrow \beta_{1}m_{k-1}+(1-\beta_{1})g_{k}$
	- Update Second Moment (estimate of gradient variance): $v_k \leftarrow \beta_2 v_{k-1} + (1-\beta_2) (g_k \circ g_k)$
	- Bias Correction: $\hat{m}_k \leftarrow m_k / (1 - \beta_1^k)$ and $\hat{v}_k \leftarrow v_k / (1 - \beta_2^k)$
	- Update Parameters: $x_k \leftarrow x_{k-1} - \alpha [\text{Diag}(\hat{v}_k)^{1/2} + \epsilon I]^{-1} \hat{m}_k$

---
# Related
```dataviewjs
// Get the tags of the current file
const currentTags = dv.current().file.tags;

// List pages from "10_Concepts"
dv.list(dv.pages('"10_Concepts"')
    .where(p => 
        // 1. Exclude the current file
        p.file.name != dv.current().file.name &&
        // 2. Check if ANY tag in the candidate page exists in currentTags
        p.file.tags.some(t => currentTags.includes(t))
    )
    .limit(10)
    .file.link
)
```

### Direct Links to this document
```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

