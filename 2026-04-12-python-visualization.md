---
title: Python 데이터 시각화 — matplotlib 실습
category: 개발
tags:
  - Python
  - matplotlib
  - numpy
  - 데이터
summary: 블로그 본문에서 바로 실행하는 Python 차트 예제 모음
date: "2026-04-12"
draft: false
---

이 블로그는 본문 안의 ` ```python ` 블록에 ▶ 실행 버튼이 생깁니다.
아래 차트들을 직접 실행해보세요!

## 사인 & 코사인 파형

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 4 * np.pi, 300)
fig, ax = plt.subplots(figsize=(8, 4))
ax.plot(x, np.sin(x), label='sin(x)', linewidth=2, color='#7c6cff')
ax.plot(x, np.cos(x), label='cos(x)', linewidth=2, linestyle='--', color='#ff6b35')
ax.set_title('사인 & 코사인 파형', fontsize=14)
ax.legend()
ax.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```

## 머신러닝 학습 곡선

```python
import matplotlib.pyplot as plt
import numpy as np

np.random.seed(42)
epochs = np.arange(1, 51)
train_loss = np.clip(np.exp(-0.07*epochs) + 0.02*np.random.randn(50), 0, None)
val_loss   = np.clip(np.exp(-0.05*epochs) + 0.08 + 0.03*np.random.randn(50), 0, None)

fig, ax = plt.subplots(figsize=(8, 4))
ax.plot(epochs, train_loss, label='Train Loss', linewidth=2, color='#7c6cff')
ax.plot(epochs, val_loss,   label='Val Loss',   linewidth=2, color='#ff6b35', linestyle='--')
ax.fill_between(epochs, train_loss, val_loss, alpha=0.08, color='gray')
ax.set_xlabel('Epoch')
ax.set_ylabel('Loss')
ax.set_title('모델 학습 곡선', fontsize=14)
ax.legend()
ax.grid(True, alpha=0.25)
plt.tight_layout()
plt.show()
```
