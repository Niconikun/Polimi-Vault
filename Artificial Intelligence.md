---
title: Artificial Intelligence
tags:
  - computer science
  - machine learning
  - automation
  - systems theory
---

# Artificial Intelligence

## Formal Definition

**Artificial Intelligence (AI)** is the branch of computer science concerned with creating machines and software systems capable of performing tasks that typically require human-level intelligence. These tasks include perception (vision, speech recognition), reasoning (problem-solving, planning), learning from data, natural language understanding, and autonomous decision-making. AI encompasses a spectrum from narrow AI (specialized for specific tasks) to the aspirational artificial general intelligence (AGI). AI is fundamental to modern engineering, enabling [[Control Systems|autonomous systems]], [[Signal Processing]], robotics, and emerging applications across aerospace, healthcare, and scientific discovery.

## Historical Development

### Key Milestones
- **1956:** Dartmouth Conference; birth of AI as academic field
- **1960s–1970s:** Expert systems; logic-based AI ("Good Old-Fashioned AI")
- **1974–1980:** First AI winter; unfulfilled promises; reduced funding
- **1980s–1990s:** Expert systems renaissance; knowledge engineering boom
- **1997:** IBM Deep Blue defeats Garry Kasparov at chess
- **2011–Present:** Deep learning revolution; neural networks exceed humans in vision, speech
- **2016:** AlphaGo defeats Lee Sedol at Go (more complex than chess)
- **2020s–Present:** Large language models, multimodal AI, generative AI (ChatGPT, GPT-4)

### Foundational Contributors
1. **Alan Turing (1912–1954):** Turing test; foundational theory of computation
2. **John McCarthy (1927–2011):** AI term coined; Lisp language; logic-based AI
3. **Marvin Minsky (1927–2016):** Neural networks; cognitive modeling; Dartmouth pioneer
4. **Geoffrey Hinton (1947–):** Deep learning revolution; backpropagation advances
5. **Yann LeCun (1960–):** Convolutional neural networks; computer vision
6. **Yoshua Bengio (1964–):** Deep learning theory; sequence models

## Core Subfields

### Machine Learning

**Definition:** Algorithms that improve performance on tasks through data-driven learning.

**Paradigms:**
1. **Supervised learning:** Learn from labeled examples (input → output)
   - Classification: Discrete outputs (cat/dog)
   - Regression: Continuous outputs (temperature prediction)

2. **Unsupervised learning:** Find patterns in unlabeled data
   - Clustering: Group similar data points
   - Dimensionality reduction: Extract latent features

3. **Reinforcement learning:** Learn through interaction and rewards
   - Agent takes actions; receives reward signal
   - Goal: Maximize cumulative reward over time

**Applications:** [[Neural Networks]], [[Kalman Filter]] (adaptive versions), autonomous vehicle control.

### Deep Learning

**Neural networks with multiple layers:**
$$
\mathbf{y} = f_n(\cdots f_2(f_1(\mathbf{x})) \cdots)
$$

**Architecture types:**
- Feedforward: Directed acyclic graph (convolutional networks)
- Recurrent: Feedback loops (LSTM, GRU for sequences)
- Attention mechanisms: Selective focus (transformers)
- Generative: Produce new data (GANs, VAE, diffusion models)

**Power:** Automatic feature learning; hierarchical representations.

### Natural Language Processing (NLP)

**Language understanding and generation:**

1. **Tokenization:** Break text into words/subwords
2. **Embedding:** Represent words as vectors
3. **Syntax/semantics:** Parse meaning
4. **Generation:** Produce coherent text

**Modern approach:** Transformer models (BERT, GPT) trained on massive text corpora.

**Applications:** Machine translation, question-answering, chatbots, code generation.

### Computer Vision

**Image/video understanding:**

1. **Image classification:** Categorize image content
2. **Object detection:** Localize and identify objects
3. **Semantic segmentation:** Pixel-level classification
4. **Instance segmentation:** Individual object boundaries
5. **3D reconstruction:** Infer 3D geometry from images

**Techniques:** Convolutional neural networks (CNNs), attention mechanisms, multimodal models.

**Aerospace applications:** Autonomous navigation, satellite image analysis, landing hazard detection.

### Robotics and Autonomous Systems

**Integration of perception, reasoning, control:**

1. **Perception:** Sensors (camera, lidar, radar) → scene understanding
2. **Planning:** Determine action sequence to achieve goal
3. **Control:** Execute plan; handle uncertainties
4. **Learning:** Improve from experience

**Challenges:** Real-time operation, safety, adaptability to new environments.

### Expert Systems and Symbolic AI

**Knowledge-based systems:**

1. **Knowledge base:** Curated facts and rules
2. **Inference engine:** Apply rules to answer queries
3. **Explanation:** Justify conclusions

**Historical importance:** 1980s boom; limitations (brittleness, knowledge bottleneck) led to AI winter.

**Resurgence:** Hybrid systems combining symbolic reasoning with neural networks.

## Mathematical Foundations

### Supervised Learning Formulation

**Given:** Training set $\{(\mathbf{x}_i, y_i)\}_{i=1}^N$

**Goal:** Learn function $f$ minimizing loss:
$$
\min_f \sum_{i=1}^N L(f(\mathbf{x}_i), y_i) + \lambda R(f)
$$

Where:
- $L$: Loss function (squared error, cross-entropy)
- $R(f)$: Regularization (prevent overfitting)
- $\lambda$: Regularization strength

**Optimization:** Gradient descent, SGD, Adam, etc.

### Neural Network Forward Pass

**Layer $\ell$:**
$$
\mathbf{z}_\ell = \mathbf{W}_\ell \mathbf{a}_{\ell-1} + \mathbf{b}_\ell
$$
$$
\mathbf{a}_\ell = \sigma(\mathbf{z}_\ell)
$$

Where:
- $\mathbf{W}_\ell, \mathbf{b}_\ell$: Weights, biases (learnable)
- $\sigma$: Activation function (ReLU, sigmoid, tanh)

**Output:** Final layer produces prediction.

### Backpropagation

**Compute gradients via chain rule:**
$$
\frac{\partial L}{\partial \mathbf{W}_\ell} = \frac{\partial L}{\partial \mathbf{z}_\ell} \frac{\partial \mathbf{z}_\ell}{\partial \mathbf{W}_\ell}
$$

**Propagate error backward through layers; update weights via gradient descent.**

**Complexity:** $O(n)$ for $n$ parameters (efficient compared to numerical gradients).

### Reinforcement Learning

**Markov Decision Process (MDP):**
$$
\pi^* = \arg\max_\pi \mathbb{E}[\sum_t \gamma^t r_t]
$$

**Value function:** Expected cumulative reward from state $s$:
$$
V(s) = \max_a \mathbb{E}[r + \gamma V(s')]
$$

**Policy:** Mapping state → action; learned to maximize value.

## Connection to Other Concepts

1. **Connection to [[Control Systems]]:**
   - AI-based control policies; learned instead of designed
   - Neural network [[Kalman Filter|observers]] and predictors

2. **Connection to [[Signal Processing]]:**
   - Feature extraction from signals
   - Sensor fusion using machine learning

3. **Connection to [[Robotics]]:**
   - Autonomous navigation
   - Object recognition and manipulation

4. **Connection to [[Machine Learning]]:**
   - Core subset of AI
   - Specific algorithms and theory

5. **Connection to [[Neural Networks]]:**
   - Key component of modern AI
   - Approximators for complex functions

## Practical Applications

### Aerospace and Space

**Autonomous spacecraft:**
- [[ADCS|Autonomous attitude determination]] using visual sensors
- Fault detection and recovery systems
- Autonomous landing hazard avoidance

**Mission planning:**
- Trajectory optimization
- Resource allocation

**Satellite operations:**
- Automated anomaly detection
- Predictive maintenance

### Autonomous Vehicles

**Perception:** Lane detection, object recognition (pedestrians, vehicles)

**Planning:** Path planning, collision avoidance

**Control:** Steering, acceleration, braking decisions

**Challenges:** Safety, edge cases, regulatory issues.

### Healthcare

**Diagnosis:** Image classification for X-rays, MRIs

**Drug discovery:** Molecular property prediction

**Treatment planning:** Personalized medicine based on patient data

### Scientific Discovery

**Physics:** Particle identification in detector data

**Chemistry:** Reaction prediction; drug design

**Astronomy:** Exoplanet discovery; object classification

**Materials science:** Predict material properties.

### Natural Language

**Machine translation:** Google Translate (transformer-based)

**Chatbots/Assistants:** Siri, Alexa, ChatGPT

**Sentiment analysis:** Social media monitoring

**Summarization:** Extract key information from text

## AI Challenges and Limitations

### Data Requirements

**Modern AI needs large datasets:**
- Supervised learning: Millions to billions of examples
- Annotation cost: Manual labeling expensive
- Data imbalance: Rare classes underrepresented

**Solutions:** Transfer learning, few-shot learning, synthetic data generation.

### Interpretability and Explainability

**Black box problem:**
- Neural networks make predictions but reasoning opaque
- Difficulty in explaining decisions

**Critical for:** Safety-critical systems (aerospace, medicine), legal compliance.

**Solutions:** Attention visualization, LIME, SHAP, symbolic AI integration.

### Robustness and Adversarial Examples

**Adversarial perturbations:**
- Tiny input changes → large output changes
- Heuristic changes (pixel values) fool classifier confidently

**Safety concern:** Autonomous vehicles misclassify perturbed signs.

**Solutions:** Adversarial training, certified robustness bounds, ensemble methods.

### Computational Cost

**Deep learning expensive:**
- Training: Weeks to months on GPUs/TPUs
- Inference: Real-time constraints problematic

**Environmental impact:** Data centers consume substantial electricity.

**Edge AI:** Compress models for on-device inference (mobile, embedded systems).

### Bias and Fairness

**AI systems learn from biased data:**
- Historical discrimination encoded in training sets
- Model perpetuates/amplifies bias

**Examples:** Facial recognition less accurate for dark-skinned people; hiring algorithms discriminate based on protected attributes.

**Mitigation:** Diverse datasets, bias audits, fairness constraints, algorithmic transparency.

## Current Frontiers

### Large Language Models (LLMs)

**Scale:** Billions to trillions of parameters

**Training:** Unsupervised learning on massive text corpora (self-supervised)

**Capabilities:** Reasoning, few-shot learning, code generation, conversational ability

**Examples:** GPT-4, Claude, Llama, PaLM

**Limitations:** Hallucination (confident incorrect statements), bias, reasoning limits

### Multimodal AI

**Multiple input types:** Text, image, audio, video combined

**Example:** Vision-language models (CLIP, GPT-4V) understand image+text

**Advantage:** Richer understanding than single modality

### Foundation Models

**Large pretrained models transferred to downstream tasks:**
- ImageNet pretrained CNN → transfer to medical imaging
- BERT pretrained language model → fine-tune for specific NLP task

**Trend:** Toward single large model for many tasks (foundation model paradigm)

### AI Alignment and Safety

**Problem:** Ensure AI systems behave as intended; aligned with human values

**Challenges:**
- Value misalignment: Subtle differences in objectives
- Specification gaming: Technically meets spec but misses intent
- Scalable oversight: How to supervise increasingly capable systems

**Research areas:** Interpretability, formal verification, robust alignment.

## See Also

- [[Machine Learning]]
- [[Neural Networks]]
- [[Control Systems]]
- [[Robotics]]
- [[Signal Processing]]
- [[Computer Vision]]
- [[Natural Language Processing]]
- [[Reinforcement Learning]]
- [[Deep Learning]]
- [[Autonomous Systems]]
