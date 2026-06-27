---
title: Machine Learning
tags:
  - artificial intelligence
  - data science
  - statistics
  - computational methods
---

# Machine Learning

## Formal Definition

**Machine learning** is a branch of [[Artificial Intelligence]] that develops computational methods enabling systems to learn from data and improve their performance on tasks without being explicitly programmed for each specific case. Machine learning algorithms identify patterns, relationships, and structures in data to make predictions, classifications, or decisions. The field combines principles from statistics, [[Linear Algebra]], [[Optimization Theory|optimization]], and computational methods to enable intelligent decision-making from empirical data.

## Historical Development

### Key Milestones
- **1950:** Alan Turing proposes "Computing Machinery and Intelligence" foundational paper
- **1966:** Perceptron algorithm introduced by Frank Rosenblatt; early neural network
- **1974–1980:** AI winter; reduced funding due to limitations of early methods
- **1980s:** Expert systems and symbolic AI gain prominence
- **1990s:** Support vector machines, ensemble methods (boosting, bagging)
- **2012:** Deep learning revolution; AlexNet wins ImageNet competition
- **2016:** AlphaGo defeats Lee Sedol in Go; transformers introduced
- **2020s:** Large language models; transformers dominate NLP; foundation models

### Foundational Contributors
1. **Arthur Samuel (1901–1990):** Checkers-playing program; coined "machine learning"
2. **Frank Rosenblatt (1928–1971):** Perceptron algorithm and neural networks
3. **Vladimir Vapnik (1935–):** Support vector machines and statistical learning theory
4. **Yann LeCun, Geoffrey Hinton, Yoshua Bengio:** Deep learning pioneers; 2018 Turing award

## Core Paradigms

### Supervised Learning

System learns from labeled training data $(x_i, y_i)$ where:
- $x_i$: input features
- $y_i$: target label or output

**Goal:** Learn mapping $f: X \to Y$ to predict $y$ from $x$.

**Regression:** Predict continuous values
$$
\hat{y} = f(x, \theta)
$$

Examples: [[Linear Quadratic Regulator|linear regression]], polynomial regression, neural networks

**Classification:** Predict discrete class labels
$$
\hat{y} = \arg\max_c P(Y = c | X = x)
$$

Examples: logistic regression, decision trees, support vector machines

### Unsupervised Learning

System learns patterns from unlabeled data $\{x_i\}$ without target values.

**Clustering:** Group similar data points
- K-means, hierarchical clustering, Gaussian mixture models
- Goal: minimize within-cluster distance, maximize between-cluster distance

**Dimensionality Reduction:** Project high-dimensional data to lower dimensions
- Principal component analysis (via [[Linear Algebra|SVD]])
- Autoencoders, t-SNE, UMAP
- Preserves important structure while reducing complexity

**Representation Learning:** Learn useful feature representations
- Word embeddings (Word2Vec, GloVe)
- Autoencoders
- Enables downstream tasks

### Reinforcement Learning

System learns through interaction and rewards:
- **Agent:** Takes actions in environment
- **State:** Current situation
- **Action:** Choice available to agent
- **Reward:** Signal indicating goodness of action
- **Policy:** Mapping from states to actions

**Goal:** Learn policy $\pi(a|s)$ maximizing cumulative reward.

**Methods:**
- [[Markov Decision Process|Q-learning]], policy gradient, actor-critic
- Temporal difference learning
- Model-based vs. model-free approaches

## Mathematical Foundation

### Loss Functions and Objective

**Empirical Risk Minimization:**
$$
\min_\theta \frac{1}{n}\sum_{i=1}^n \mathcal{L}(f(x_i; \theta), y_i) + \lambda R(\theta)
$$

Where:
- $\mathcal{L}$: loss function (measures prediction error)
- $R(\theta)$: regularization term (prevents overfitting)
- $\lambda$: regularization parameter

**Common Loss Functions:**

1. **Regression:**
   - Mean squared error: $\mathcal{L} = \frac{1}{n}\sum(y_i - \hat{y}_i)^2$
   - Mean absolute error: $\mathcal{L} = \frac{1}{n}\sum|y_i - \hat{y}_i|$

2. **Classification:**
   - [[Cross-entropy]] loss: $\mathcal{L} = -y_i \log(\hat{y}_i) - (1-y_i)\log(1-\hat{y}_i)$
   - Hinge loss (SVM): $\mathcal{L} = \max(0, 1 - y_i \hat{y}_i)$

### Optimization

**Gradient Descent:**
$$
\theta_{t+1} = \theta_t - \eta \nabla_\theta \mathcal{L}(\theta_t)
$$

Where $\eta$ is learning rate.

**Variants:**
- Stochastic gradient descent (SGD): Update on mini-batches
- Momentum methods: Adam, RMSprop (adaptive learning rates)
- Second-order methods: Newton's method, L-BFGS

### Regularization

**L1 Regularization (Lasso):**
$$
R(\theta) = \|\theta\|_1 = \sum_i |\theta_i|
$$
Encourages sparsity (feature selection).

**L2 Regularization (Ridge):**
$$
R(\theta) = \|\theta\|_2^2 = \sum_i \theta_i^2
$$
Encourages small weights; smoother models.

**Dropout:** Randomly deactivate neurons during training (prevents co-adaptation).

## Model Architectures

### Linear Models

**Linear Regression:** $f(x) = w^T x + b$

**Logistic Regression:** $f(x) = \sigma(w^T x + b)$ where $\sigma$ is sigmoid

**Support Vector Machines:** Find maximum-margin separating hyperplane

### Decision Trees and Ensembles

**Decision Trees:** Recursive binary splits; interpretable but prone to overfitting

**Random Forests:** Ensemble of trees; reduces variance through averaging

**Gradient Boosting:** Sequential trees; each corrects previous; state-of-the-art for tabular data

### Neural Networks

**Feedforward Networks:** Layers of neurons with nonlinear activation functions
$$
h^{(l+1)} = \sigma(W^{(l)} h^{(l)} + b^{(l)})
$$

**Convolutional Neural Networks (CNNs):** Exploit spatial structure; excellent for images

**Recurrent Neural Networks (RNNs):** Process sequences; [[Markov]] assumption relaxed
- Long Short-Term Memory (LSTM)
- Gated Recurrent Unit (GRU)

**Transformers:** Attention mechanisms; dominates NLP
- Self-attention: Learn which tokens to focus on
- Multi-head attention: Parallel attention computations
- Enables parallel processing; excellent scalability

## Learning Theory

### Generalization

**Training Error:** Error on training data
$$
E_{\text{train}} = \frac{1}{n}\sum_{i=1}^n \mathcal{L}(f(x_i), y_i)
$$

**Test Error:** Error on unseen test data (what we care about)
$$
E_{\text{test}} = E_{(x,y) \sim \text{test dist}}[\mathcal{L}(f(x), y)]
$$

**Overfitting:** $E_{\text{test}} \gg E_{\text{train}}$ (model memorizes training data)

**Underfitting:** Both errors large (model too simple)

### Bias-Variance Tradeoff

$$
E[(f(x) - y)^2] = \text{Bias}^2(f) + \text{Var}(f) + \sigma^2_{\text{noise}}
$$

- **Bias:** Error from wrong model assumptions
- **Variance:** Sensitivity to training data fluctuations
- Complex models reduce bias but increase variance

### VC Dimension and PAC Learning

**Vapnik-Chervonenkis Dimension:** Capacity measure of hypothesis class

**Probably Approximately Correct (PAC) Learning:** Theoretical guarantees on sample complexity

## Key Algorithms and Methods

### Supervised Learning Algorithms

1. **Linear Models:** Analytical solution via normal equations or [[Least Squares Method]]
2. **SVM:** Quadratic programming; kernel tricks for nonlinearity
3. **Decision Trees:** Information gain or Gini impurity splits
4. **Random Forests:** Bootstrap aggregating; parallel tree training
5. **Gradient Boosting:** Sequential [[Optimization Theory|optimization]]; XGBoost, LightGBM
6. **Neural Networks:** Backpropagation; [[Optimization Theory|stochastic gradient descent]]

### Unsupervised Learning Algorithms

1. **K-Means:** Alternating cluster assignment and centroid updates
2. **Hierarchical Clustering:** Agglomerative or divisive merging
3. **PCA:** [[Linear Algebra|Eigenvalue decomposition]] or SVD of data covariance
4. **Autoencoder:** Neural network reconstruction loss
5. **Gaussian Mixture Models:** Expectation-maximization (EM) algorithm

### Reinforcement Learning Algorithms

1. **Q-Learning:** Off-policy value function approximation
2. **Policy Gradient:** Direct policy optimization
3. **Actor-Critic:** Combines value and policy learning
4. **PPO/A3C:** Modern efficient methods

## Practical Considerations

### Data Preprocessing

- **Normalization/Standardization:** Rescale features to comparable scales
- **Handling Missing Data:** Imputation strategies
- **Feature Engineering:** Domain knowledge to create informative features
- **Class Imbalance:** Resampling, weighted losses, SMOTE

### Model Evaluation

**Regression Metrics:**
- Mean squared error (MSE), root MSE
- Mean absolute error
- $R^2$ coefficient of determination

**Classification Metrics:**
- Accuracy, precision, recall, F1 score
- ROC-AUC curve
- Confusion matrix

**Cross-Validation:** K-fold validation estimates generalization error

### Hyperparameter Tuning

- **Grid Search:** Exhaustive parameter combinations
- **Random Search:** Random parameter sampling
- **Bayesian Optimization:** Probabilistic model-guided search
- **Early Stopping:** Stop training when validation error plateaus

## Applications

### Computer Vision

- **Image Classification:** Identify objects in images
- **Object Detection:** Locate and classify multiple objects
- **Semantic Segmentation:** Pixel-level classification
- **Face Recognition:** Identify individuals

### Natural Language Processing

- **Text Classification:** Sentiment analysis, spam detection
- **Machine Translation:** Sequence-to-sequence models
- **Question Answering:** Comprehension and retrieval
- **Large Language Models:** GPT family; few-shot learning

### Recommendation Systems

- **Collaborative Filtering:** Learn from user-item interactions
- **Content-Based:** Feature similarity
- **Hybrid:** Combine multiple signals
- Critical for e-commerce, streaming platforms

### Control and Robotics

- **Imitation Learning:** Learn from demonstrations
- **Reinforcement Learning:** Autonomous control policies
- **Path Planning:** Navigate complex environments
- **Adaptive Control:** [[Adaptive Control Theory]] combined with learning

### Finance and Economics

- **Price Prediction:** Time series forecasting
- **Portfolio Optimization:** Asset allocation
- **Fraud Detection:** Anomaly detection
- **Credit Scoring:** Risk assessment

## Relationship to Other Concepts

1. **Connection to [[Statistics]]:**
   - [[Normal Distribution]], hypothesis testing
   - Maximum likelihood estimation

2. **Connection to [[Linear Algebra]]:**
   - Matrix operations in neural networks
   - [[QR Decomposition]], eigenvalue methods

3. **Connection to [[Optimization Theory]]:**
   - Gradient descent, convex optimization
   - Lagrange multipliers

4. **Connection to [[Control Systems]]:**
   - Adaptive control via learning
   - Reinforcement learning for autonomous systems

5. **Connection to [[Artificial Intelligence]]:**
   - Subset of AI methods
   - Enables intelligent decision-making

## Modern Challenges and Future Directions

### Current Limitations

- **Data Efficiency:** Require massive datasets
- **Interpretability:** "Black box" nature of deep learning
- **Robustness:** Vulnerable to adversarial perturbations
- **Fairness:** Bias amplification from biased training data
- **Computational Cost:** Training transformers requires enormous compute

### Future Directions

- **Few-Shot Learning:** Learn from limited examples
- **Transfer Learning:** Leverage pre-trained models
- **Meta-Learning:** Learn to learn
- **Causal Inference:** Distinguish correlation from causation
- **Continual Learning:** Online adaptation to new data

## See Also

- [[Artificial Intelligence]]
- [[Statistics]]
- [[Linear Algebra]]
- [[Optimization Theory]]
- [[Neural Networks]]
- [[Control Systems]]
- [[Signal Processing]]
- [[Reinforcement Learning]]
- [[Gradient Descent]]
- [[Markov Decision Process]]
