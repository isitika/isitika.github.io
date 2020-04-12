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

슈트라센 알고리즘은 이름 그대로 독일의 수학자 폴커 슈트라센(Volker Strassen)이 만든 행렬 곱 연산을 빠르게 수행하기 위해 만든 알고리즘이다.



#### 2.행렬의 곱셈

크기가 n x n인 두 행렬 A와B의 곱을 C로 나타내보자.

일단 행렬 A와 B를 2x2행렬로 나타내어 보면

A=  \begin{bmatrix}
      A_{1,1}&A_{1,2}\\
      A_{2,1}&A_{2,2} 
      \end{bmatrix}

B= \begin{bmatrix}
      B_{1,1}&B_{1,2}\\
      B_{2,1}&B_{2,2} 
     \end{bmatrix}

로나타내어 지고

그의 곱인 C는

C= \begin{bmatrix}
      A_{1,1}*B_{1,1}+A_{1,2}*B_{2,1}&A_{1,1}*B_{1,2}+A_{1,2}*B_{2,2}\\
      A_{2,1}*B_{1,1}+A_{2,2}*B_{2,1}&A_{2,1}*B_{1,2}+A_{2,2}*B_{2,2}
     \end{bmatrix}

로 나타내어 진다.

#### 3.스트라센 알고리즘 



A와 B를 체 F에 대한 정사각행렬이라고 하자. 두 행렬의 곱 C는 다음과 같다.![](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4c680ec4a32379114e0326ba69b179881b69e8e)
만약 A와 B가 2n × 2n 꼴의 크기가 아니라면 먼저 모자라는 행과 열을 0으로 채운다. 이 경우 행렬 곱셈이 끝난 뒤 행렬에서 필요한 부분만 다시 잘라 내야 한다.

이제 A, B, C를 같은 크기의 정사각행렬 네 개로 나눈다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)

이 때,

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2948b2c6caf12770b217310b956b23abdc80380)

따라서 다음이 성립한다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)

이 과정에서는 필요한 연산의 수가 줄어 들지 않는다. 여전히 *Ci,j* 행렬을 계산하려면 여덟 번의 곱셈과 네 번의 덧셈이 필요하다.

이제 다음과 같은 행렬을 정의한다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/1e9e6268d824de7ad5010a32a1921452b264f7ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d40beeba8019e378fa0ed4b6e549c44a140a9ec)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/45e8e9679d33f2c66e24bd812e1e554f95bb1571)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/c12df2bb70f8f09f33f1ca4b8c2d577d5850a2ee)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/715adfa757b74b3ad6b4eea545c24762e4079161)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/30107b9c9c99494bf75f23e84b505e5921cee46e)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e93ef1c265be8be96209dde36230d56e139fc72)

이 *Mk* 행렬들은 *Ci,j* 행렬을 표현하는 데 쓰이는데, 이 행렬들을 계산하는 데는 일곱 번의 곱셈(각 변수마다 한 번씩)과 10번의 덧셈이 필요하다. 이제 *Ci,j* 행렬은 다음과 같이 표현할 수 있다.

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/26875b8ca1815e2c322c798faeecabe1d7836798)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/e71779a8ecc64f3e1268485cf389a05cdd3e6bf8)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5853fa11f016df7eee4eb2a7ceb6137d3b3296de)

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b7d7d4ee9e67e0c23f1a522787d4829072542dbb)



이 과정에서는 곱셈이 사용되지 않기 때문에, 전체 곱셈을 일곱 번의 곱셈과 18번의 덧셈으로 처리할 수 있다. 큰 행렬에 대해서는 행렬의 곱셈이 덧셈보다 더 많은 시간을 필요로 하기 때문에 덧셈을 더 하는 대신 곱셈을 덜 하는 것이 전체적으로 더 효율적이다.



이 과정에서는 곱셈이 사용되지 않기 때문에, 전체 곱셈을 일곱 번의 곱셈과 18번의 덧셈으로 처리할 수 있다. 큰 행렬에 대해서는 행렬의 곱셈이 덧셈보다 더 많은 시간을 필요로 하기 때문에 덧셈을 더 하는 대신 곱셈을 덜 하는 것이 전체적으로 더 효율적이다.

이 과정을 재귀적으로 반복할 경우 총 ![{\displaystyle 7\cdot n^{\log _{2}7}-6\cdot n^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/586e85e6ba93daf1db18e144da90a79af278e9a9)번의 연산이 필요하다. ![{\displaystyle \log _{2}7=2.807\cdots }](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce05babfc0fc45343915cfe440346e34e8442bfe)이므로 전체 수행 시간은 약 O(n2.807)이다. 실제로는 *n*이 작을 경우 정의에 따라 행렬 곱셈을 하는 경우가 빠를 수도 있기 때문에, 보통 작은 *n*에 대해서는 일반적인 방법으로 곱셈을 하도록 구현한다.

슈트라센 알고리즘은 속도에 비해 수치 안정성이 떨어지는 것으로 알려져 있다. 두 행렬 *A*와 *B*를 곱한 결과를 *C*라 할 때, 실제 오차인![](https://wikimedia.org/api/rest_v1/media/math/render/svg/892fed34761231c6ae447382f89caa717b376a46) 보다 작음이 알려져 있다. 이는 일반적인 행렬 곱셈보다 더 큰 오차이다

#### 4.스트라센 알고리즘의 사용

O-Notation 상의 속도는 더 빠르나, 

i) Starssen Algorithm은 재귀적으로 돌려 시간이 오래걸리며, 반복적 알고리즘으로 바꾸는데 어렵다.

ii) P,Q,R,S,T,U,V를 담아둘 자리를 기억장치 안에 마련해야 하므로, 행렬이 클 경우 자리를 너무 많이 차지한다.



실제 컴퓨터에서 돌리면, 속도가 더 느리게 나온다고 하는데

이는 Strassen Algorithm의 O-Notation앞에 엄청 큰 상수가 곱해지기 때문이다.

따라서, Strassen Algorithm이 행렬의 곱셈 보다 더 빠르게 수행되기 위해선 엄청 큰 n이 필요하며

너무 큰 n의 크기에 의해 주로 슈퍼 컴퓨터에 사용된다.

 

Strassen Algorithm의 놀라운 점은 O(n^3)의 속도가 깨지지 않을 것이라 생각했는데

이보다 작은 시간이 나왔다는 것이 놀라운 이유이다.

#### 5.출처

[https://ko.wikipedia.org/wiki/%EC%8A%88%ED%8A%B8%EB%9D%BC%EC%84%BC_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98](https://ko.wikipedia.org/wiki/슈트라센_알고리즘)

https://m.blog.naver.com/PostView.nhn?blogId=babobigi&logNo=220502327816&proxyReferer=https%3A%2F%2Fwww.google.com%2F

