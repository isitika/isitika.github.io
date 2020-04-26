---
layout: single
title: Starssen Algorithm
date: 2020-04-26 21:00:00 +0900
author: dongJin
use_math: true
---



# 그리디 알고리즘 

### 1.그리디 알고리즘이란?

그리디 알고리즘이란, 문제를 최적화하하여 푸는데 사용되는 알고리즘이다. 즉, 문제를 가장 좋은 답을 찾는 알고리즘 중 하나다. 

그리디라는 단어 에서 알 수 있듯이, 그리디 알고리즘은 가장 좋은 것 만을 고르는 알고리즘이다. 하지만 여기서 가장 좋은 것이란 요소들과의 관계나 미래의 일은 생각하지 않고 고른 것이다. 그렇기 때문에 만약 그것을 고르고 이전의 것을 버리는 것이 더 좋은 선택이더라도 그리디 알고리즘은 그것을 고려하지 않는다.

그렇기 때문에 단순히 최고의 것을 고르는 것이 아니게 되어 복잡해지면 그리디 알고리즘은 최선의 선택을 하지 못 한다. 그렇기에 그리디 알고리즘은 단순한 문제에 적합하다. 하지만 "지금 상황에서만 가장 좋은 것을 찾는다"라는 단순한 조건 때문에 어떤 것이 가장 좋은것인지만 설정하면 문제를 해결하기가 쉬워서 종종 꼭 가장 최적화된 값을 찾는 문제가 아니면 이 알고리즘을 사용하기도 한다. 

### 2.DNA문제

그리디 알고리즘을 구하던 중 간단하지만 우리가 과학시간때나 평소에 들어본 DNA에 관한 문제(백준1969번 문제 https://www.acmicpc.net/problem/1969)를 찾게 되었다.

DNA는 DeoxyriboNucleic Acid의 약자로 사람몸을 구성하는 분자인데 이 DNA는 보통 4가지의 핵염기 아데닌,구아닌,티민,사이토신으로 만들어진다. 이를 각각 단어의 앞글자를 따서 A,G,T,C로 표현한다. 즉 아데닌-티민-사이토신-구아닌 으로 이루어진 DNA는 "ATCG"로 표현된다.

그리고 해밍거리(Hamming Distance)란 두 DNA가 있을때 서로 다른 핵염기의 개수이다.

EX) "ATCGGCA" "ATCCAGA" 이 두개의 해밍거리는 3개이다.

여기서 문제는 n개의 DNA가 주어졌을때, 해밍거리가 최소인 DNA를 구하는 것이다. 단, 그 DNA의 값이 여러개 나오면 사전순(A-T-G-C)으로 봐서 가장 앞에 있는 DNA를 선택한다. 

과연 이 해밍거리가 최소인 DNA를 어떻게 구할까?

이를 그리디알고리즘을 사용해 구해보면 해밍거리를 최소화 할려면 똑같은 줄에서 DNA를 최대한 겹쳐야한다.  즉 DNA를 만들때 원래의 DNA에서 각 줄에서 가장 많이 나온 핵염기를 선택해서 DNA를 구성하면 된다. 

예를 들어 링크의 문제 예제 2를 보면

"ACGTACGTAC"
"CCGTACGTAG"
"GCGTACGTAT"
"TCGTACGTAA"

가 주어 지면 각각 1번째에서는 핵염기가 전부 있으므로 A, 2번재에서는 C가 가장 많이 있으므로 C,.....이런 식으로 선택해서 최종적으로 "ACGTACGTAA"를 선택한다. 그리고 첫번째에서는 1개 두번째에서는2개 세번째에서는 2개 세번째에서는 1개로 해밍거리는 6이된다.



이를 java코드로 구성해보면 다음과 같이 구성 할 수 있다.



```java
import java.util.Scanner;

public class Main{
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        int i, j;
        int n = sc.nextInt();
        int m = sc.nextInt();
        int max = 0;
        int hd = 0;
        int a, t, g, c;
        char ch;
        String[] DNA = new String[n];
        for (i = 0; i < n; i++) {
            DNA[i] = sc.next();
        }
        for (i = 0; i < m; i++) {
            a = 0;
            t = 0;
            g = 0;
            c = 0;
            for (j = 0; j < n; j++) {
                if (DNA[j].charAt(i) == 'A') {
                    a++;
                } else if (DNA[j].charAt(i) == 'T') {
                    t++;
                } else if (DNA[j].charAt(i) == 'G') {
                    g++;
                } else if (DNA[j].charAt(i) == 'C') {
                    c++;
                }
            }
            max = Math.max(a > c ? a : c, g > t ? g : t);
            hd += (n - max);
            if (max == a) ch = 'A';
            else if (max == c) ch = 'C';
            else if (max == g) ch = 'G';
            else ch = 'T';
            System.out.print(ch);
        }
        System.out.println("\n" + hd);
        sc.close();
      }
    }

```









