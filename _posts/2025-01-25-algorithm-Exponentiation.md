---
title: "빠른 모듈러 거듭제곱 알고리즘 이해하기"
categories:
  - algorithm
  - math
  - cryptology
tags:
  - 거듭제곱
  - 모듈러 연산
  - 빠른 거듭제곱
  - 알고리즘
---

# 빠른 모듈러 거듭제곱 알고리즘 이해하기

---

## **목차**

1. [들어가며](#들어가며)
2. [기본 개념 이해하기](#기본-개념-이해하기)
3. [왜 빠른 거듭제곱 알고리즘이 필요한가요?](#왜-빠른-거듭제곱-알고리즘이-필요한가요)
4. [빠른 거듭제곱 알고리즘의 아이디어](#빠른-거듭제곱-알고리즘의-아이디어)
5. [단계별로 쉽게 살펴보기](#단계별로-쉽게-살펴보기)
6. [지수가 홀수일 때의 처리 방법](#지수가-홀수일-때의-처리-방법)
7. [알고리즘 작동 과정 예시](#알고리즘-작동-과정-예시)
8. [알고리즘의 핵심 요약](#알고리즘의-핵심-요약)
9. [코드 구현](#코드-구현)
10. [결론](#결론)
11. [참고 자료](#참고-자료)

---

## 들어가며

**빠른 모듈러 거듭제곱 알고리즘**은 큰 수의 거듭제곱을 효율적으로 계산하기 위한 방법입니다. 특히 모듈러 연산과 결합하여 큰 수 계산에서 중간 값이 너무 커지는 것을 방지하며 정확한 결과를 빠르게 얻을 수 있습니다.

---

## 기본 개념 이해하기

### 거듭제곱 (Exponentiation)

- 어떤 수를 여러 번 곱하는 연산입니다.
- **예**: \( 2^5 = 2 \times 2 \times 2 \times 2 \times 2 = 32 \)

### 모듈러 연산 (Modulo Operation)

- 어떤 수를 다른 수로 **나눈 나머지**를 구하는 연산입니다.
- **표현**: \( a \mod m \)
- **예**: \( 17 \mod 5 = 2 \) (17을 5로 나눈 나머지는 2)

### 모듈러 거듭제곱

- 거듭제곱 결과를 특정 수로 나눈 나머지를 구하는 것.
- **예**: \( 3^4 \mod 5 = 81 \mod 5 = 1 \)

---

## 왜 빠른 거듭제곱 알고리즘이 필요한가요?

- **큰 지수의 거듭제곱**은 계산량이 매우 많습니다.
  - **예**: \( 2^{1000} \)은 \( 2 \)를 1000번 곱해야 합니다.
- **효율적인 계산 방법**이 없다면 실제로 계산하기 어렵습니다.
- **빠른 거듭제곱 알고리즘**은 계산 횟수를 **대폭 줄여줍니다**.

---

## 빠른 거듭제곱 알고리즘의 아이디어

### 거듭제곱의 성질 활용

- **지수법칙**을 사용하여 계산을 단순화합니다.

#### 지수법칙

1. **지수가 짝수일 때**:
   \[
   a^{n} = \left( a^{\frac{n}{2}} \right)^2
   \]
2. **지수가 홀수일 때**:
   \[
   a^{n} = a \times \left( a^{\frac{n-1}{2}} \right)^2
   \]

---

## 단계별로 쉽게 살펴보기

### 예시: \( 5^{13} \mod 100 \) 계산

#### 초기 설정

- `result = 1`
- `base = 5`
- `exponent = 13`

#### 반복 과정

1. **exponent = 13 (홀수)**
   - `result = (result * base) % 100 = (1 * 5) % 100 = 5`
   - `base = (base * base) % 100 = (5 * 5) % 100 = 25`
   - `exponent = 13 // 2 = 6`

2. **exponent = 6 (짝수)**
   - `base = (base * base) % 100 = (25 * 25) % 100 = 25`
   - `exponent = 6 // 2 = 3`

3. **exponent = 3 (홀수)**
   - `result = (result * base) % 100 = (5 * 25) % 100 = 25`
   - `base = (base * base) % 100 = (25 * 25) % 100 = 25`
   - `exponent = 3 // 2 = 1`

4. **exponent = 1 (홀수)**
   - `result = (result * base) % 100 = (25 * 25) % 100 = 25`
   - `base = (base * base) % 100 = (25 * 25) % 100 = 25`
   - `exponent = 1 // 2 = 0`

#### 최종 결과

- `result = 25`
- 따라서 \( 5^{13} \mod 100 = 25 \)

---

## 지수가 홀수일 때의 처리 방법

### 왜 결과에 기반을 곱하는가?

- 지수가 홀수이면 짝수로 만들어서 계산하는 것이 효율적입니다.
- 수학적으로:
  \[
  a^{2k+1} = a \times \left( a^{k} \right)^2
  \]
- 따라서, **결과(result)에 현재의 기반(base)을 곱하고**, 지수를 1 감소시켜 짝수로 만듭니다.

---

## 알고리즘 작동 과정 예시

### 예시: \( 2^7 \mod m \) 계산 (m은 임의의 모듈러 값)

#### 초기값

- `result = 1`
- `base = 2`
- `exponent = 7`

#### 반복 과정

1. **exponent = 7 (홀수)**
   - `result = (result * base) % m`
   - `base = (base * base) % m`
   - `exponent = (exponent - 1) // 2`

2. **exponent = 3 (홀수)**
   - `result = (result * base) % m`
   - `base = (base * base) % m`
   - `exponent = (exponent - 1) // 2`

3. **exponent = 1 (홀수)**
   - `result = (result * base) % m`
   - `base = (base * base) % m`
   - `exponent = (exponent - 1) // 2`

#### 최종 결과

- 지수가 0이 될 때까지 반복하여 `result`를 구합니다.

---

## 알고리즘의 핵심 요약

- **기반(base)을 제곱하면서** 지수를 절반으로 줄여나갑니다.
- **지수가 홀수일 때**는 결과(result)에 기반(base)을 한 번 더 곱해주어 지수를 짝수로 만듭니다.
- 이 과정을 지수가 0이 될 때까지 반복합니다.

---

## 코드 구현

```cpp
#include <iostream>

// 모듈러 거듭제곱 함수
long long mod_pow(long long base, long long exponent, long long modulus) {
    long long result = 1;
    base = base % modulus; // 초기 기반 값을 modulus로 나눔

    while (exponent > 0) {
        if (exponent % 2 == 1) { // 지수가 홀수인 경우
            result = (result * base) % modulus; // 결과에 기반을 곱하고 모듈러 연산
        }
        base = (base * base) % modulus; // 기반을 제곱하고 모듈러 연산
        exponent /= 2; // 지수를 절반으로 감소
    }
    return result;
}

int main() {
    long long a, n, m;
    std::cout << "a^n mod m을 계산합니다.\n";
    std::cout << "a를 입력하세요: ";
    std::cin >> a;
    std::cout << "n을 입력하세요: ";
    std::cin >> n;
    std::cout << "m을 입력하세요: ";
    std::cin >> m;

    long long result = mod_pow(a, n, m);
    std::cout << "결과: " << result << std::endl;
    return 0;
}