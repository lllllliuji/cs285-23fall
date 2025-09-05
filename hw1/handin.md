# 1. Analysis

## Task 1.  Show that $\sum_{s_t}|p_{\pi_{\theta} }(s_t) - p_{\pi^\star}(s_t)|\le  2T\epsilon$  

1. 对$p_{\pi_{\theta} }(s_t)$做展开：
   $$
      \mathbb{p_{\pi_{\theta}}}(s_t) =  (1 - \epsilon) ^ {t} p_{\pi^{\star}}(s_t) + (1 - (1- \epsilon) ^ {t})p_{mistake}(s_t)
   $$
   其中$(1- \epsilon) ^ {t}$为不犯错的概率，$(1 - (1- \epsilon) ^ {t})$为至少犯错一次的概率。
2. 代入原式：
   $$
   \begin{align}
      \sum_{s_t} |p_{\pi_{\theta}}(s_t) - p_{\pi^{\star}}(s_t)|
      &= \sum_{s_t}| (1 - \epsilon) ^ {t}  p_{\pi^{\star}}(s_t) + (1 - (1- \epsilon) ^ {t}) .p_{mistake}(s_t) - p_{\pi^{\star}}(s_t)| \\
      &= \sum_{s_t}(1 - (1- \epsilon) ^ {t})| p_{mistake}(s_t) - p_{\pi^{\star}}(s_t)| \\
      &\le 2\sum_{s_t}(1 - (1- \epsilon) ^ {t}) \\
      &\le 2T\epsilon
   \end{align}
   $$
   其中，（3）式由TV距离(total variation distance)的定义推导而来，其最大值为2，（4）式由union bound inequality推导而来。至少犯错一次的概率小于等于各个事件发生概率的和

### Task 2

### (a) 只考虑最终状态的奖励

对于所有$t < T,$$r(s_t)$ = 0,所以有
$$\begin{align}
   J(\pi) &= \sum_{t = 1} ^{T}\mathbb{E}_{p_{\pi}(s_t)}r(s_t) \\
   &= \mathbb{E}_{p_\pi(s_T)}r(s_T)
\end{align}
$$
从而，
   $$  
   \begin{align}
      J(\pi^{\star}) - J(\pi_{\theta}) &=  \mathbb{E}_{p_{\pi^\star}(s_T)} r(s_T) - \mathbb{E}_{p_{\pi_\theta}(s_T)} r(s_T)   \\
      &= \sum_{s_T}P_{\pi^\star}(s_T) r(s_T) - \sum_{s_T}P_{\pi_\theta}(s_T)r(s_T) \\
      &= \sum_{s_T}r(s_T)(P_{\pi^\star}(s_T) - P_{\pi_\theta}(s_T)) \\
      &\le R_{max}\sum_{s_T}(P_{\pi^\star}(s_T) - P_{\pi_\theta}(s_T))  \\
      &\le R_{max}\sum_{s_T}|P_{\pi^\star}(s_T) - P_{\pi_\theta}(s_T)|
   \end{align}
   $$
由task1的结论可得，$J(\pi^{\star}) - J(\pi_{\theta}) \le 2R_{max}T\epsilon$，$J(\pi^*) - J(\pi_\theta) = \mathcal{O}(T \varepsilon)$原题得证。

### (b) 考虑任意奖励

 可以根据(a)的结论轻易证明，
 $$  
   \begin{align}
      J(\pi^{\star}) - J(\pi_{\theta}) &=  \sum_{t = 1}^{T}\mathbb{E}_{p_{\pi^\star}(s_t)} r(s_t) - \mathbb{E}_{p_{\pi_\theta}(s_t)} r(s_t)   \\
      &\le R_{max}\sum_{t=1}^{T}\mathbb{E}_{p_{\pi^\star}(s_t)} - \mathbb{E}_{p_{\pi_\theta}(s_t)} \\
      &\le 2R_{max}T^{2}\epsilon
   \end{align}
   $$
   $J(\pi^*) - J(\pi_\theta) = \mathcal{O}(T^2 \varepsilon)$原题得证。  
