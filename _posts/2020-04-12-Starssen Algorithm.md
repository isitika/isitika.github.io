---
layout: single
title: Starssen Algorithm
date: 2020-04-12 21:00:00 +0900
author: dongJin
use_math: true
---

스트라센 알고리즘
=============

#### 1.개요

스트라센 알고리즘은 이름 그대로 독일의 수학자 폴커 스트라센(Volker Strassen)이 만든 행렬 곱 연산을 빠르게 수행하기 위해 만든 알고리즘이다.



#### 2.행렬의 곱셈

크기가 n x n인 두 행렬 A와B의 곱을 C로 나타내보자.

일단 행렬 A와 B를 2x2행렬로 나타내어 보면

A =\begin{bmatrix}\mathbf {A} _{1,1}&\mathbf {A} _{1,2}\\\ \mathbf {A} _{2,1}&\mathbf {A} _{2,2}\end{bmatrix}

B =\begin{bmatrix}\mathbf {B} _{1,1}&\mathbf {B} _{1,2}\\\ \mathbf {B} _{2,1}&\mathbf {B} _{2,2}\end{bmatrix}

로나타내어 지고

그의 곱인 C는

C= \begin{bmatrix}\mathbf {A} _{1,1}\mathbf {B} _{1,1}+\mathbf {A} _{1,2}\mathbf {B} _{2,1}&\mathbf {A} _{1,1}\mathbf {B} _{1,2}+\mathbf {A} _{1,2}\mathbf {B} _{2,2}\\\ \mathbf {A} _{2,1}\mathbf {B} _{1,1}+\mathbf {A} _{2,2}\mathbf {B} _{2,1}&\mathbf {A} _{2,1}\mathbf {B} _{1,2}+\mathbf {A} _{2,2}\mathbf {B} _{2,2}\end{bmatrix}

로나타내어 진다.

그리고 이 행렬곱의 수행시간은 행렬곱인 C의 nxn개의 원소에서 n번에 곱셉을하므로 n의 3제곱의 수행시간을 가지고 있다.

#### 3.스트라센 알고리즘 

스트라센 알고리즘은 이 행렬곱을 곱셉을 조금 더 사용하지 않고 계산하기 위해 만들어 졌다.

 M이라는 수식을 미리 표현해 놓고 행렬곱을 표현하는데 M은 다음과 같다

![{\displaystyle \mathbf {M} _{1}:=(\mathbf {A} _{1,1}+\mathbf {A} _{2,2})(\mathbf {B} _{1,1}+\mathbf {B} _{2,2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)

![{\displaystyle \mathbf {M} _{2}:=(\mathbf {A} _{2,1}+\mathbf {A} _{2,2})\mathbf {B} _{1,1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)

![{\displaystyle \mathbf {M} _{3}:=\mathbf {A} _{1,1}(\mathbf {B} _{1,2}-\mathbf {B} _{2,2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)

![{\displaystyle \mathbf {M} _{4}:=\mathbf {A} _{2,2}(\mathbf {B} _{2,1}-\mathbf {B} _{1,1})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)

![{\displaystyle \mathbf {M} _{5}:=(\mathbf {A} _{1,1}+\mathbf {A} _{1,2})\mathbf {B} _{2,2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)

![{\displaystyle \mathbf {M} _{6}:=(\mathbf {A} _{2,1}-\mathbf {A} _{1,1})(\mathbf {B} _{1,1}+\mathbf {B} _{1,2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)

![{\displaystyle \mathbf {M} _{7}:=(\mathbf {A} _{1,2}-\mathbf {A} _{2,2})(\mathbf {B} _{2,1}+\mathbf {B} _{2,2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)

그리고 이제 이 M으로 2x2행렬곱의 결과인 C를 만들면

![{\displaystyle \mathbf {C} _{1,1}=\mathbf {M} _{1}+\mathbf {M} _{4}-\mathbf {M} _{5}+\mathbf {M} _{7}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)

![{\displaystyle \mathbf {C} _{1,2}=\mathbf {M} _{3}+\mathbf {M} _{5}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)

![{\displaystyle \mathbf {C} _{2,1}=\mathbf {M} _{2}+\mathbf {M} _{4}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)

![{\displaystyle \mathbf {C} _{2,2}=\mathbf {M} _{1}-\mathbf {M} _{2}+\mathbf {M} _{3}+\mathbf {M} _{6}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)



이 *Mk* 행렬들은 *Ci,j* 행렬을 표현하는 데 쓰이는데, 이 행렬들을 계산하는 데는 일곱 번의 곱셈(각 변수마다 한 번씩)과 10번의 덧셈이 필요하다. 이제 *Ci,j* 행렬은 다음과 같이 표현할 수 있다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)











