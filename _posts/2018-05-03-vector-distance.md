---
layout: post
title: 벡터 거리
tags: [수학]
excerpt_separator: <!--more-->
---

벡터 거리 계산
<!--more-->

### 유클리드 거리

일반적으로 유클리드 계산식은 다음과 같다. 임의의 벡터 $$\mathbf{x}$$에 대한 모든 벡터공간에서 Euclidian norm $$\Vert\mathbf{x}\Vert_2 = \sqrt{\sum_{i=1}^n \|x_i\|^2 }$$을 따르며, 여기서 $$n$$은 차원을 나타낸다.

$$
d(\mathbf{p}, \mathbf{q}) = \sqrt{(q_1-p_1)^2+\cdots+(q_n-p_n)^2} = \sqrt{\sum_{i=1}^n (q_i-p_i)^2}
$$

### 두 점 사이의 거리

$$n = 2$$일 때 다음과 같이 계산한다.

$$
d(\mathbf{p}, \mathbf{q}) = \sqrt{(q_1-p_1)^2+(q_2-p_2)^2}
$$

### 참고 자료

- [KaTeX guide](http://sixthform.info/katex/guide.html)
- [KaTeX demo](https://tiddlywiki.com/plugins/tiddlywiki/katex/)