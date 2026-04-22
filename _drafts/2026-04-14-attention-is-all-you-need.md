---
layout: post
title: "[논문 리뷰] Attention Is All You Need"
description: >
  Transformer 아키텍처를 처음 제안한 2017년 NLP 핵심 논문 리뷰입니다.
categories: [research]
tags: [논문리뷰, transformer, NLP, deep-learning]
sitemap: true
---

## 논문 정보

- **제목**: Attention Is All You Need
- **저자**: Vaswani et al. (Google Brain)
- **연도**: 2017
- **링크**: [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)

---

## 핵심 아이디어

기존 seq2seq 모델은 RNN/LSTM 기반으로 순차 처리가 필요해 **병렬화가 불가능**했습니다.  
이 논문은 RNN을 완전히 제거하고, **Attention 메커니즘만으로** 시퀀스를 처리하는 Transformer를 제안합니다.

## Scaled Dot-Product Attention

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

- **Q (Query)**: 현재 위치가 어떤 정보를 찾는지
- **K (Key)**: 각 위치가 어떤 정보를 제공하는지
- **V (Value)**: 실제로 가져올 정보

$\sqrt{d_k}$로 나누는 이유는 내적값이 커지면 softmax 기울기가 사라지는 것을 방지하기 위함입니다.

## Multi-Head Attention

Attention을 $h$번 병렬로 수행한 뒤 결합합니다.

```python
class MultiHeadAttention(nn.Module):
    def __init__(self, d_model, num_heads):
        super().__init__()
        self.d_k = d_model // num_heads
        self.heads = num_heads
        self.W_q = nn.Linear(d_model, d_model)
        self.W_k = nn.Linear(d_model, d_model)
        self.W_v = nn.Linear(d_model, d_model)
        self.W_o = nn.Linear(d_model, d_model)

    def forward(self, Q, K, V):
        # 각 head별로 attention 계산
        ...
```

## Positional Encoding

Transformer는 순서 정보가 없으므로 위치 정보를 직접 주입합니다.

$$
PE_{(pos, 2i)} = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)
$$

## 정리

| 항목 | RNN | Transformer |
|------|-----|-------------|
| 병렬화 | 불가 | 가능 |
| 장거리 의존성 | 약함 | 강함 |
| 학습 속도 | 느림 | 빠름 |

> 이 논문 이후 BERT, GPT 등 현대 LLM의 기초가 되었습니다.
