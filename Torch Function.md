# Torch Function

[TOC]

## torch.distributions

### Normal

```python
import torch
from torch.distributions import Normal
mean = torch.tensor([0,1])
normal = Normal(mean, 1)
normal: Normal(loc: torch.Size([2]), scale: torch.Size([2]))
# 这里的意思其实就是会进行个broadcast，构建多个分布

# sample()
normal.sample() <=>
torch.normal(mean=normal.loc, std=normal.scale)
# 采样出的size是和normal中分布的size一样，注意一个分布按照它自己的规律进行独立采样

# rsample()
normal.esample() <=>
rsample()不是在定义的正太分布上采样，而是先对标准正太分布N(0,1)进行采样，然后输出：mean + std × 采样值

# log_prob(value)
log_prob(value)是计算value在定义的正态分布（mean,1）中对应的概率的对数，正太分布概率密度函数是
这里我们通过对数概率还原其对应的真实概率：
normal.log_prob(x).exp()
# 这里必须保证x和normal可以进行broadcast
# 这里的prob就是，横坐标为x，它所对应的在分布上的概率
```

$$
f(x)=\frac{1}{\sqrt{2 \pi} \sigma} e^{-\frac{(x-\mu)^{2}}{2 \sigma^{2}}}
$$

对其取对数得
$$
\log (f(x))=-\frac{(x-\mu)^{2}}{2 \sigma^{2}}-\log (\sigma)-\log (\sqrt{2 \pi})
$$
