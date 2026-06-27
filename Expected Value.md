## Formal Definition

**Expected Value** (also known as **expectation**, **mathematical expectation**, or **mean**) is a fundamental concept in [[probability theory]] that represents the weighted average of all possible values of a random variable, where each value is weighted by its probability of occurrence. For a discrete random variable, it is computed as a sum of values multiplied by their probabilities; for a continuous random variable, it is calculated as an integral of the value multiplied by its [[Probability Density Function (PDF)]]. The expected value provides a measure of the central tendency of a distribution and represents the long-term average outcome if an experiment were repeated infinitely many times.

## Historical Development

### Key Milestones
- **1654:** Blaise Pascal and Pierre de Fermat establish foundational concepts in their correspondence on gambling problems
- **1657:** Christiaan Huygens publishes *De Ratiociniis in Ludo Aleae*, formally introducing expectation
- **1713:** Jacob Bernoulli proves the Law of Large Numbers, connecting expectation to long-term averages
- **1812:** Pierre-Simon Laplace formalizes expectation for continuous variables in *Théorie Analytique des Probabilités*
- **1933:** Andrey Kolmogorov provides measure-theoretic definition in *Foundations of the Theory of Probability*
- **1940s:** Development of conditional expectation and martingale theory
- **1950s-60s:** Extension to Banach spaces and operator theory
- **1970s-present:** Applications in finance, economics, and machine learning

### Foundational Contributors
1. **Blaise Pascal (1623-1662):** Early work on expectation in gambling problems
2. **Christiaan Huygens (1629-1695):** First formal definition of expectation
3. **Jacob Bernoulli (1655-1705):** Law of Large Numbers connecting expectation to averages
4. **Pierre-Simon Laplace (1749-1827):** Extension to continuous variables
5. **Andrey Kolmogorov (1903-1987):** Measure-theoretic formalization
6. **Joseph Doob (1910-2004):** Development of martingale theory

## Mathematical Formulation

### General Form

For a random variable \(X\) defined on probability space \((\Omega, \mathcal{F}, P)\):
- **Discrete case:**
  $$
  E[X] = \sum_{x \in \mathcal{X}} x \cdot P(X = x)
  $$
  where \(\mathcal{X}\) is the countable support of \(X\)

- **Continuous case:**
  $$
  E[X] = \int_{-\infty}^{\infty} x \cdot f_X(x) \, dx
  $$
  where \(f_X\) is the [[Probability Density Function (PDF)]]

- **General measure-theoretic:**
  $$
  E[X] = \int_\Omega X(\omega) \, dP(\omega)
  $$
  as a Lebesgue integral

### Component Breakdown

**Probability Weighting:** Each value weighted by its probability/density  
**Summation/Integration:** Over all possible values  
**Existence Condition:** Requires \(E[|X|] < \infty\) (absolute integrability)

### Special Cases
1. **Indicator Function:** For event \(A\), \(E[I_A] = P(A)\)
2. **Constant:** \(E[c] = c\)
3. **Linear Transformation:** \(E[aX + b] = aE[X] + b\)
4. **Non-negative Variables:** \(E[X] = \int_0^\infty P(X > x) \, dx\) for \(X \geq 0\)

## Fundamental Principles

### Linearity of Expectation
For any random variables \(X, Y\) and constants \(a, b\):
$$
E[aX + bY] = aE[X] + bE[Y]
$$
This holds **regardless of dependence** between \(X\) and \(Y\).

### Law of the Unconscious Statistician (LOTUS)
For measurable function \(g\):
- **Discrete:** \(E[g(X)] = \sum_x g(x)P(X = x)\)
- **Continuous:** \(E[g(X)] = \int_{-\infty}^\infty g(x)f_X(x) \, dx\)

### Monotonicity
If \(X \leq Y\) almost surely, then \(E[X] \leq E[Y]\)

### Expectation of Products
For independent \(X, Y\):
$$
E[XY] = E[X]E[Y]
$$
(Converse not necessarily true)

## Theoretical Framework

### Measure-Theoretic Foundation
Expected value is the Lebesgue integral of the random variable with respect to the probability measure:
- **Simple functions:** Finite linear combinations of indicator functions
- **Non-negative functions:** Supremum of expectations of simple functions
- **General functions:** \(E[X] = E[X^+] - E[X^-]\) when both finite

### Existence and Finiteness
- **Finite expectation:** \(E[|X|] < \infty\)
- **Infinite expectation:** \(E[|X|] = \infty\) (e.g., Cauchy distribution)
- **Non-existent:** When \(E[X^+] = E[X^-] = \infty\)

### Convergence Theorems
1. **Monotone Convergence:** If \(0 \leq X_n \uparrow X\), then \(E[X_n] \uparrow E[X]\)
2. **Fatou's Lemma:** \(E[\liminf X_n] \leq \liminf E[X_n]\)
3. **Dominated Convergence:** If \(|X_n| \leq Y\) with \(E[Y] < \infty\) and \(X_n \to X\), then \(E[X_n] \to E[X]\)

## Classification and Variants

### By Type of Variable
1. **Discrete expectation:** Sum over countable support
2. **Continuous expectation:** Integral with density
3. **Mixed expectation:** Combination of discrete and continuous parts

### Conditional Expectation
- **Definition:** \(E[X|Y]\) is random variable representing expectation given information in \(Y\)
- **Properties:** Tower property, taking out what's known
- **Interpretation:** Best predictor in mean-square sense

### Higher-Order Expectations
1. **Moments:** \(E[X^k]\) for \(k = 1, 2, \dots\)
2. **Central moments:** \(E[(X - E[X])^k]\)
3. **Absolute moments:** \(E[|X|^k]\)

### Vector-Valued Expectation
For random vector \(\mathbf{X} = (X_1, \dots, X_n)\):
$$
E[\mathbf{X}] = (E[X_1], \dots, E[X_n])
$$

## Derivation and Proof

### From First Principles

**Discrete Case Derivation:**
Given probabilities \(p_i = P(X = x_i)\), the weighted average:
$$
E[X] = \sum_{i=1}^\infty x_i p_i
$$
provided \(\sum |x_i| p_i < \infty\).

**Continuous Case Derivation:**
Using Riemann-Stieltjes/Lebesgue integral:
$$
E[X] = \int_{-\infty}^\infty x \, dF_X(x)
$$
where \(F_X\) is [[Cumulative Distribution Function (CDF)]].

### Proof of Linearity

**For simple functions:** \(X = \sum a_i I_{A_i}\), \(Y = \sum b_j I_{B_j}\)
$$
E[aX + bY] = \sum_i a a_i P(A_i) + \sum_j b b_j P(B_j) = aE[X] + bE[Y]
$$

**Extension to general functions:** Via monotone convergence and approximation.

### Law of Large Numbers Proof Sketch

**Strong LLN:** For i.i.d. \(X_i\) with \(E[|X_1|] < \infty\):
$$
\frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{a.s.} E[X_1]
$$
Proof uses Kolmogorov's inequality and Borel-Cantelli lemmas.

## Physical Interpretation

### Center of Mass Analogy
For probability distribution as mass distribution:
- **Expected value:** Center of mass/balance point
- **Variance:** Moment of inertia about center

### Long-Run Average
In repeated independent trials:
- **Sample mean:** \(\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i\)
- **Convergence:** \(\bar{X}_n \to E[X]\) as \(n \to \infty\) (LLN)

### Fair Value in Gambling
- **St. Petersburg paradox:** Highlighted need for expected utility theory
- **Fair price:** Expected value represents fair price of gamble
- **Risk premium:** Difference between expected value and certainty equivalent

### Information-Theoretic View
Expected value minimizes mean squared error:
$$
E[X] = \arg\min_{c \in \mathbb{R}} E[(X - c)^2]
$$

## Applications

### Statistics & Data Science
1. **Parameter estimation:** Sample mean as estimator of population mean
2. **Bias-variance tradeoff:** Expected prediction error decomposition
3. **Loss functions:** Expected loss minimization in statistical learning
4. **Bootstrap methods:** Estimating sampling distributions

### Economics & Finance
1. **Expected utility:** Decision making under uncertainty
2. **Asset pricing:** Expected returns in CAPM, arbitrage pricing
3. **Option pricing:** Risk-neutral expectations in Black-Scholes
4. **Insurance:** Premium calculation as expected loss plus loading

### Engineering & Physics
1. **[[Signal processing]]:** Expected value as DC component
2. **Statistical mechanics:** Ensemble averages
3. **Reliability engineering:** Expected time to failure
4. **[[Control theory]]:** Expected cost in stochastic control

### Computer Science
1. **Randomized algorithms:** Expected running time analysis
2. **[[Information theory]]:** Expected code length
3. **[[Machine learning]]:** Expected risk minimization
4. **[[Game theory]]:** Expected payoff in mixed strategies

## Implementation Considerations

### Numerical Computation

**Discrete Expectation:**
```python
def discrete_expectation(values, probabilities):
    """Compute expectation for discrete RV"""
    return sum(v * p for v, p in zip(values, probabilities))

# Example: Dice roll
values = [1, 2, 3, 4, 5, 6]
probs = [1/6] * 6
E_dice = discrete_expectation(values, probs)  # 3.5
```

**Continuous Expectation (Numerical Integration):**
```python
import numpy as np
from scipy import integrate, stats

def continuous_expectation(pdf, support=(-np.inf, np.inf)):
    """Compute expectation via numerical integration"""
    result = integrate.quad(lambda x: x * pdf(x), 
                           support[0], support[1])
    return result[0]

# [[Normal distribution]]
normal_expectation = continuous_expectation(
    lambda x: stats.norm.pdf(x, 0, 1),
    (-10, 10)  # Truncated for numerical stability
)
```

**Monte Carlo Estimation:**
```python
def monte_carlo_expectation(sampler, g=None, n=10000):
    """Estimate E[g(X)] via Monte Carlo"""
    samples = sampler(n)
    if g is None:
        return np.mean(samples)
    else:
        return np.mean(g(samples))

# Example: E[X^2] for standard normal
samples = np.random.randn(100000)
E_X2 = np.mean(samples**2)  # Approximately 1
```

### Specialized Methods
1. **Importance sampling:** For rare events or peaked distributions
2. **Control variates:** Variance reduction technique
3. **Antithetic variates:** Using negatively correlated samples
4. **Conditional Monte Carlo:** Conditioning on partial information

### Computational Complexity
- **Direct summation:** O(n) for n possible values
- **Numerical integration:** O(1/ε^d) for d dimensions (curse of dimensionality)
- **Monte Carlo:** O(1/√n) convergence rate, independent of dimension

## Advantages and Limitations

### Strengths
1. **Mathematical tractability:** Linear, easy to compute and manipulate
2. **Intuitive interpretation:** Center of distribution, long-run average
3. **Foundational role:** Basis for variance, [[covariance]], and other moments
4. **Universal applicability:** Works for discrete, continuous, and mixed variables

### Weaknesses
1. **Sensitivity to outliers:** Heavy-tailed distributions can have infinite expectation
2. **Incomplete information:** Single number doesn't capture shape or tails
3. **Existence issues:** Not all random variables have finite expectation (e.g., Cauchy)
4. **Risk neutrality:** Doesn't account for risk aversion in decision making

### Validity Range
- **Well-defined:** When \(E[|X|] < \infty\)
- **Problematic:** For heavy-tailed distributions (Pareto with α ≤ 1)
- **Misleading:** For multimodal or highly skewed distributions

## Advanced Topics

### Conditional Expectation
- **Definition:** \(E[X|\mathcal{G}]\) for σ-algebra \(\mathcal{G}\)
- **Properties:** Linearity, tower property, taking out what's known
- **Interpretation:** Best \(\mathcal{G}\)-measurable approximation of \(X\) in L²

### Martingale Theory
- **Martingale:** \(E[X_{n+1}|X_1,\dots,X_n] = X_n\)
- **Submartingale:** \(E[X_{n+1}|X_1,\dots,X_n] \geq X_n\)
- **Applications:** Stochastic calculus, financial mathematics

### Fat-Tailed Distributions
- **Infinite mean:** When integral/sum diverges
- **Pareto distribution:** \(f(x) \sim x^{-α-1}\), finite mean if α > 1
- **Implications:** Law of Large Numbers may fail

### Higher-Dimensional Expectations
- **Random matrices:** Expected eigenvalues, traces
- **Functional data:** Expectations in function spaces
- **Stochastic processes:** Expected paths, expected occupation measures

## Special Cases and Examples

### Common Distributions
1. **Bernoulli(p):** \(E[X] = p\)
2. **Binomial(n, p):** \(E[X] = np\)
3. **Poisson(λ):** \(E[X] = λ\)
4. **Exponential(λ):** \(E[X] = 1/λ\)
5. **Normal(μ, σ²):** \(E[X] = μ\)
6. **Uniform(a, b):** \(E[X] = (a+b)/2\)

### Interesting Counterexamples
1. **Cauchy distribution:** No finite expectation
2. **St. Petersburg paradox:** Infinite expected value with finite utility
3. **Pareto with α=1:** Infinite mean (Zipf's law)

### Multivariate Examples
1. **Multivariate normal:** \(E[\mathbf{X}] = \mathbf{μ}\)
2. **Wishart distribution:** \(E[W] = n\Sigma\)
3. **Dirichlet distribution:** \(E[X_i] = α_i / \sum_j α_j\)

## Error Analysis

### Estimation Error
**Sample mean error:**
- **Bias:** \(E[\bar{X}_n] - μ = 0\) (unbiased)
- **Variance:** \(Var(\bar{X}_n) = σ²/n\)
- **Mean squared error:** \(MSE = σ²/n\)

**Confidence intervals:**
For large n, by CLT:
$$
P\left(\left|\bar{X}_n - μ\right| > z_{α/2}\frac{σ}{\sqrt{n}}\right) ≈ α
$$

### Numerical Integration Error
- **Quadrature rules:** Error ~ O(n^{-k}) for smooth functions
- **Adaptive quadrature:** Automatic error control
- **Monte Carlo error:** Standard error = σ/√n

### Model Misspecification Error
- **Wrong distribution:** Bias in expectation estimation
- **Heavy tails:** Underestimation of risk
- **[[Dependence]]:** Invalid independence assumptions

## Relationship to Other Concepts

### Connection to Variance
Variance is expected squared deviation from mean:
$$
Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2
$$

### Relation to Generating Functions
- **Moment generating function:** \(M_X(t) = E[e^{tX}]\)
- **[[Characteristic function]]:** \(\phi_X(t) = E[e^{itX}]\)
- **Cumulant generating function:** \(K_X(t) = \log E[e^{tX}]\)

### Contrast with Median and Mode
- **Mean (expectation):** Sensitive to outliers, minimizes squared error
- **Median:** Robust to outliers, minimizes absolute error
- **Mode:** Most frequent value, may not be unique

### Link to Law of Large Numbers
Strong LLN: For i.i.d. \(X_i\) with \(E[|X_1|] < ∞\):
$$
\frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{a.s.} E[X_1]
$$

## Historical Context and Evolution

### Early Development
- **Gambling origins:** Pascal and Fermat solving division of stakes problem
- **Huygens' expectation:** Formal definition as fair price
- **Bernoulli's utility:** Resolution of St. Petersburg paradox via expected utility

### Modern Formalization
- **Kolmogorov's axioms:** Measure-theoretic foundation
- **Doob's martingale theory:** Conditional expectation and stochastic processes
- **Von Neumann-Morgenstern:** Expected utility theory in economics

### Current Frontiers
- **Robust statistics:** Estimators less sensitive to outliers
- **High-dimensional statistics:** Expectation in hundreds of dimensions
- **Online learning:** Streaming computation of expectations
- **Causal inference:** Expected potential outcomes

## Pedagogical Approach

### Teaching Strategies
1. **Gambling examples:** Fair games, expected winnings
2. **Physical analogies:** Center of mass, balance point
3. **Simulation demonstrations:** Law of Large Numbers visualization
4. **Gradual abstraction:** From finite to countable to continuous

### Common Misconceptions
1. **"Expected value = most likely value":** Not true for skewed distributions
2. **"Expected value always exists":** Cauchy distribution has no mean
3. **"Expected value equals sample mean for small samples":** Only true in limit
4. **"Linearity requires independence":** Linearity holds regardless of dependence

### Learning Resources
- **Textbooks:** Ross's *A First Course in Probability*, Williams' *Probability with Martingales*
- **Online:** Khan Academy Probability, MIT 6.041 Probabilistic Systems Analysis
- **Visualization:** Seeing Theory (seeingtheory.org), Distributome
- **Software:** R, Python (numpy, scipy), Jupyter notebooks

## Implementation Examples

### Python Comprehensive Implementation

```python
import numpy as np
from scipy import integrate, stats
from abc import ABC, abstractmethod

class ExpectationCalculator(ABC):
    """Abstract base class for expectation calculation"""
    
    @abstractmethod
    def expectation(self, g=None):
        """Compute E[g(X)]"""
        pass
    
    @abstractmethod
    def sample(self, n=1):
        """Generate samples from distribution"""
        pass
    
    def monte_carlo_expectation(self, g=None, n=10000):
        """Estimate expectation via Monte Carlo"""
        samples = self.sample(n)
        if g is None:
            return np.mean(samples)
        else:
            return np.mean(g(samples))
    
    def variance(self):
        """Compute variance = E[X^2] - (E[X])^2"""
        EX = self.expectation()
        EX2 = self.expectation(lambda x: x**2)
        return EX2 - EX**2

class DiscreteDistribution(ExpectationCalculator):
    """Discrete distribution with finite support"""
    
    def __init__(self, values, probabilities):
        self.values = np.array(values)
        self.probabilities = np.array(probabilities)
        self.probabilities /= self.probabilities.sum()  # Normalize
        
    def expectation(self, g=None):
        if g is None:
            return np.sum(self.values * self.probabilities)
        else:
            g_values = g(self.values)
            return np.sum(g_values * self.probabilities)
    
    def sample(self, n=1):
        return np.random.choice(self.values, size=n, p=self.probabilities)

class ContinuousDistribution(ExpectationCalculator):
    """Continuous distribution defined by PDF"""
    
    def __init__(self, pdf, support=(-np.inf, np.inf), 
                 cdf=None, sampling_func=None):
        self.pdf = pdf
        self.support = support
        self.cdf = cdf
        self.sampling_func = sampling_func
        
    def expectation(self, g=None):
        if g is None:
            integrand = lambda x: x * self.pdf(x)
        else:
            integrand = lambda x: g(x) * self.pdf(x)
        
        result, error = integrate.quad(integrand, 
                                      self.support[0], 
                                      self.support[1])
        return result
    
    def sample(self, n=1):
        if self.sampling_func:
            return self.sampling_func(n)
        else:
            # Inverse transform sampling if CDF available
            if self.cdf:
                # Need inverse CDF - approximate numerically
                u = np.random.uniform(0, 1, n)
                # Simple numerical inversion (for demonstration)
                from scipy.optimize import brentq
                samples = []
                for ui in u:
                    # Find x such that CDF(x) = ui
                    try:
                        x_root = brentq(lambda x: self.cdf(x) - ui, 
                                       self.support[0], 
                                       self.support[1])
                        samples.append(x_root)
                    except:
                        # Fallback to rejection sampling
                        samples.append(self._rejection_sample())
                return np.array(samples)
            else:
                # Rejection sampling
                return self._rejection_sampling(n)
    
    def _rejection_sampling(self, n):
        """Basic rejection sampling implementation"""
        a, b = self.support
        if not np.isfinite(a) or not np.isfinite(b):
            # Estimate support from PDF (crude)
            x_test = np.linspace(-10, 10, 1000)
            pdf_test = self.pdf(x_test)
            mask = pdf_test > 1e-10
            a, b = x_test[mask][0], x_test[mask][-1]
        
        # Find maximum of PDF
        x_grid = np.linspace(a, b, 1000)
        y_grid = self.pdf(x_grid)
        M = np.max(y_grid) * 1.1
        
        samples = []
        while len(samples) < n:
            x_prop = np.random.uniform(a, b)
            y_prop = np.random.uniform(0, M)
            
            if y_prop < self.pdf(x_prop):
                samples.append(x_prop)
        
        return np.array(samples)

# Predefined distributions
class NormalDistribution(ContinuousDistribution):
    def __init__(self, mu=0, sigma=1):
        self.mu = mu
        self.sigma = sigma
        
        pdf = lambda x: (1/(sigma*np.sqrt(2*np.pi))) * \
                       np.exp(-0.5*((x-mu)/sigma)**2)
        cdf = lambda x: 0.5 * (1 + stats.erf((x-mu)/(sigma*np.sqrt(2))))
        sampling_func = lambda n: np.random.normal(mu, sigma, n)
        
        super().__init__(pdf, (-np.inf, np.inf), cdf, sampling_func)
    
    def expectation(self, g=None):
        # Analytic for normal
        if g is None:
            return self.mu
        else:
            return super().expectation(g)

class ExponentialDistribution(ContinuousDistribution):
    def __init__(self, lam=1):
        self.lam = lam
        
        pdf = lambda x: lam * np.exp(-lam*x) if x >= 0 else 0
        cdf = lambda x: 1 - np.exp(-lam*x) if x >= 0 else 0
        sampling_func = lambda n: np.random.exponential(1/lam, n)
        
        super().__init__(pdf, (0, np.inf), cdf, sampling_func)
    
    def expectation(self, g=None):
        if g is None:
            return 1/self.lam
        else:
            return super().expectation(g)

# Expectation properties demonstration
def demonstrate_expectation_properties():
    print("="*60)
    print("Expectation Properties Demonstration")
    print("="*60)
    
    # 1. Linearity demonstration
    print("\n1. Linearity of Expectation")
    
    # Two correlated dice
    n_samples = 100000
    X = np.random.randint(1, 7, n_samples)  # First die
    Y = X + np.random.randint(0, 2, n_samples)  # Correlated with first
    
    # Direct computation
    Z = 2*X + 3*Y
    E_Z_direct = np.mean(Z)
    
    # Using linearity
    E_X = np.mean(X)
    E_Y = np.mean(Y)
    E_Z_linear = 2*E_X + 3*E_Y
    
    print(f"   E[2X + 3Y] (direct): {E_Z_direct:.4f}")
    print(f"   E[2X + 3Y] (linearity): {E_Z_linear:.4f}")
    print(f"   Difference: {abs(E_Z_direct - E_Z_linear):.6f}")
    
    # 2. LOTUS demonstration
    print("\n2. Law of the Unconscious Statistician (LOTUS)")
    
    # [[Normal distribution]]
    normal = NormalDistribution(0, 1)
    samples = normal.sample(10000)
    
    # E[sin(X)] for X ~ N(0,1)
    E_sin_direct = np.mean(np.sin(samples))
    
    # Numerical integration for comparison
    f = lambda x: np.sin(x) * stats.norm.pdf(x, 0, 1)
    E_sin_integral = integrate.quad(f, -10, 10)[0]
    
    print(f"   E[sin(X)] (Monte Carlo): {E_sin_direct:.6f}")
    print(f"   E[sin(X)] (integration): {E_sin_integral:.6f}")
    
    # 3. Conditional expectation demonstration
    print("\n3. Conditional Expectation")
    
    # Simple example: E[X | X > 0] for standard normal
    samples = normal.sample(100000)
    conditional_samples = samples[samples > 0]
    E_cond = np.mean(conditional_samples)
    
    # Theoretical: E[X | X > 0] = √(2/π) for standard normal
    theoretical = np.sqrt(2/np.pi)
    
    print(f"   E[X | X > 0] (empirical): {E_cond:.6f}")
    print(f"   E[X | X > 0] (theoretical): {theoretical:.6f}")
    
    # 4. Variance via expectation
    print("\n4. Variance = E[X^2] - (E[X])^2")
    
    exp_dist = ExponentialDistribution(2)
    samples = exp_dist.sample(10000)
    
    # Direct variance calculation
    var_direct = np.var(samples)
    
    # Using expectation
    E_X = np.mean(samples)
    E_X2 = np.mean(samples**2)
    var_expectation = E_X2 - E_X**2
    
    print(f"   Var(X) (direct): {var_direct:.6f}")
    print(f"   Var(X) (via expectations): {var_expectation:.6f}")
    
    # 5. Law of Large Numbers demonstration
    print("\n5. Law of Large Numbers")
    
    sample_sizes = [10, 100, 1000, 10000, 100000]
    true_mean = 0.5  # For Uniform(0,1)
    
    print("\n   Sample size | Sample mean | Error")
    print("   " + "-"*40)
    
    for n in sample_sizes:
        samples = np.random.uniform(0, 1, n)
        sample_mean = np.mean(samples)
        error = abs(sample_mean - true_mean)
        print(f"   {n:11d} | {sample_mean:11.6f} | {error:9.6f}")
    
    # 6. Expectation of functions
    print("\n6. Expectation of Various Functions")
    
    X_dist = NormalDistribution(0, 1)
    
    functions = [
        ("X^2", lambda x: x**2),
        ("|X|", lambda x: np.abs(x)),
        ("exp(X)", lambda x: np.exp(x)),
        ("X * I(X>0)", lambda x: x * (x > 0))
    ]
    
    print("\n   Function | Analytical | Monte Carlo (n=100k)")
    print("   " + "-"*45)
    
    for name, func in functions:
        # Monte Carlo
        samples = X_dist.sample(100000)
        mc_estimate = np.mean(func(samples))
        
        # Analytical where known
        if name == "X^2":
            analytical = 1  # Var(X) = 1 for N(0,1)
        elif name == "|X|":
            analytical = np.sqrt(2/np.pi)
        elif name == "exp(X)":
            analytical = np.exp(0.5)  # MGF at t=1: exp(σ²/2)
        elif name == "X * I(X>0)":
            analytical = 1/np.sqrt(2*np.pi)
        else:
            analytical = None
        
        if analytical is not None:
            print(f"   {name:10} | {analytical:10.6f} | {mc_estimate:10.6f}")
        else:
            print(f"   {name:10} | {'--':10} | {mc_estimate:10.6f}")
    
    # Visualization
    print("\n7. Generating visualizations...")
    
    import matplotlib.pyplot as plt
    
    # Plot 1: Law of Large Numbers
    plt.figure(figsize=(12, 10))
    
    plt.subplot(2, 2, 1)
    n_points = 1000
    samples = np.random.uniform(0, 1, n_points)
    running_means = np.cumsum(samples) / np.arange(1, n_points + 1)
    
    plt.plot(range(1, n_points + 1), running_means, 'b-', alpha=0.7)
    plt.axhline(y=0.5, color='r', linestyle='--', label='True mean')
    plt.xlabel('Sample size')
    plt.ylabel('Sample mean')
    plt.title('Law of Large Numbers')
    plt.legend()
    plt.grid(alpha=0.3)
    
    # Plot 2: Expectation as center of mass
    plt.subplot(2, 2, 2)
    
    # [[Normal distribution]]
    x = np.linspace(-4, 4, 1000)
    pdf = stats.norm.pdf(x, 0, 1)
    
    plt.plot(x, pdf, 'b-', linewidth=2, label='PDF')
    plt.fill_between(x, pdf, alpha=0.3)
    
    # Mark expectation
    plt.axvline(x=0, color='r', linestyle='--', linewidth=2, label='E[X]')
    
    plt.xlabel('x')
    plt.ylabel('Density')
    plt.title('Expectation as Center of Mass')
    plt.legend()
    plt.grid(alpha=0.3)
    
    # Plot 3: Linearity demonstration
    plt.subplot(2, 2, 3)
    
    # Two independent distributions
    X_vals = np.random.normal(0, 1, 10000)
    Y_vals = np.random.exponential(1, 10000)
    
    Z_vals = 2*X_vals + 3*Y_vals
    
    # Plot histograms
    plt.hist(X_vals, bins=50, alpha=0.5, density=True, label='X~N(0,1)')
    plt.hist(Y_vals, bins=50, alpha=0.5, density=True, label='Y~Exp(1)')
    plt.hist(Z_vals, bins=50, alpha=0.5, density=True, label='Z=2X+3Y')
    
    # Mark expectations
    plt.axvline(x=0, color='blue', linestyle=':', label='E[X]=0')
    plt.axvline(x=1, color='orange', linestyle=':', label='E[Y]=1')
    plt.axvline(x=3, color='green', linestyle=':', label='E[Z]=3')
    
    plt.xlabel('Value')
    plt.ylabel('Density')
    plt.title('Linearity of Expectation')
    plt.legend()
    plt.grid(alpha=0.3)
    
    # Plot 4: Conditional expectation
    plt.subplot(2, 2, 4)
    
    # Standard normal truncated to positive values
    samples = np.random.normal(0, 1, 10000)
    pos_samples = samples[samples > 0]
    
    plt.hist(samples, bins=50, alpha=0.5, density=True, label='Full distribution')
    plt.hist(pos_samples, bins=25, alpha=0.7, density=True, 
             label='Conditional on X>0')
    
    # Mark expectations
    plt.axvline(x=0, color='black', linestyle='-', alpha=0.5)
    plt.axvline(x=0, color='blue', linestyle=':', label='E[X]=0')
    plt.axvline(x=np.sqrt(2/np.pi), color='red', linestyle=':', 
                label='E[X|X>0]')
    
    plt.xlabel('x')
    plt.ylabel('Density')
    plt.title('Conditional Expectation')
    plt.legend()
    plt.grid(alpha=0.3)
    
    plt.tight_layout()
    plt.show()
    
    # Advanced: Convergence rates
    print("\n8. Convergence Rates Comparison")
    
    distributions = [
        ("Normal(0,1)", lambda: np.random.normal(0, 1)),
        ("Exp(1)", lambda: np.random.exponential(1)),
        ("Cauchy", lambda: np.random.standard_cauchy())
    ]
    
    sample_sizes = [10, 100, 1000, 10000]
    
    plt.figure(figsize=(10, 6))
    
    for dist_name, sampler in distributions:
        errors = []
        for n in sample_sizes:
            # Estimate mean for this sample size
            sample_means = []
            for _ in range(100):  # Repeat for stability
                samples = sampler(n)
                sample_means.append(np.mean(samples))
            
            # For Cauchy, true mean doesn't exist - use median of sample means
            if dist_name == "Cauchy":
                errors.append(np.median(np.abs(sample_means)))
            else:
                errors.append(np.mean(np.abs(sample_means)))
        
        plt.loglog(sample_sizes, errors, 'o-', label=dist_name)
    
    plt.plot(sample_sizes, 1/np.sqrt(sample_sizes), 'k--', 
             label='1/√n reference')
    plt.xlabel('Sample size (log scale)')
    plt.ylabel('Absolute error (log scale)')
    plt.title('Convergence of Sample Mean to Expectation')
    plt.legend()
    plt.grid(alpha=0.3, which='both')
    plt.show()

if __name__ == "__main__":
    demonstrate_expectation_properties()
```

## See Also

- [[Variance]]
- [[Moment (Mathematics)]]
- [[Law of Large Numbers]]
- [[Conditional Expectation]]
- [[Linearity of Expectation]]
- [[Law of the Unconscious Statistician]]
- [[Sample Mean]]
- [[Probability Distribution]]
- [[Random Variable]]
- [[Monte Carlo Method]]
- [[Characteristic Function]]
- [[Moment Generating Function]]
- [[Fatou's Lemma]]
- [[Monotone Convergence Theorem]]
- [[Dominated Convergence Theorem]]

---

**Note:** Expected value is the cornerstone of [[probability theory]] and statistical inference. It provides the fundamental link between probability distributions and their numerical characteristics, serving as the basis for most statistical analyses, decision-making under uncertainty, and stochastic modeling. Understanding its properties, limitations, and computational aspects is essential for any quantitative discipline.

---
*Template adapted from Obsidian Technical Concept Template | Last Updated: 2025-04-11*

---