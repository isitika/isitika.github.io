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

이 만들어진다.

여기서 M에서 곱셈을 각각 7번을 하고 그 이후로는 덧셈만을 이용하므로 행렬곱에서 8번 곱셈을 하는 것보다 곱셈을 덜 하게 된다.

만약 이 곱셈을 덜 하고 덧셈을 더 하는 것을 재귀적으로 반복하여 식으로 나타내면 ![{\displaystyle 7\cdot n^{\log _{2}7}-6\cdot n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/586e85e6ba93daf1db18e144da90a79af278e9a9) 번의 연산이 필요한 것으로 나온다,

여기서  \log _{2}7=2.807 이므로 총 연산시간은 n의 약2.8 제곱이다.

스트라센 알고리즘은 행렬곱 계산에서 참신한 방법으로 연산시간을 n의 3제곱에서 더 줄여주는다.

하지만 이 스트라센 알고리즘이 컴퓨터에서 행렬곱연산에 쓰일 때는 M이라는 수식을 만들어 저장해야할 공간도 있어야 하고 n의 숫자가 작을 때는 위에서 볼때 와 같이 식에 덧셈이 많아져 연산시간이 더 걸려 비효율적일 수 있다.

하지만 n의 숫자가 많아질수록 점차 스트라센의 알고리즘의 연산시간이 더 적어지므로 큰 행렬끼리의 곱을 계산 할 때 더 시간을 단축시킬 수 있으므로 전체적으로 효율적인 알고리즘이라고 볼 수 있다.

 









