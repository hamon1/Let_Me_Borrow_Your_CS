Cache Memory
======
### 캐시 메모리
CPU는 프로그램을 실행하는 과정에서 메모리에 저장된 데이터를 빈번하게 사용한다.
하지만 메모리에 접근하는 시간은 연산 속도보다 느리다. 
이 차이를 극복하기 위하여 탄생한 것이 캐시 메모리이다.

----
#### 저장 장치 계층 구조
_일반적인 저장 장치는 (1. CPU와 가까운 장치는 빠르고, 멀리 있는 장치는 느리다. 2. 속도가 빠른 장치는 저장 용량이 작고, 가격이 비싸다.) 라는 명제를 따른다._

컴퓨터가 사용하는 저장 장치들은 'CPU에 얼마나 가까운가'를 기준으로 계층적으로 나타낼 수 있다.
이 것을 저장 장치 계층 구조(memory hierarchy)라고 한다.

<br>

- 레지스터
- 캐시 메모리
  - L1
  - L2
  - L3
- 메모리
- 보조기억장치

> _(위로 갈 수록, 속도 증가, 용량 감소, 가격 증가)_
----
#### 캐시 메모리
캐시 메모리는 CPU와 메모리 사이에 위치하고, 레지스터보다 용량이 크고 메모리보다 빠른 SRAM 기반의 저장 장치이다.

메모리에서 CPU가 사용할 일부 데이터를 미리 캐시 메모리로 가지고 와서 활용하는 것이다.
_(비유하자면, 물건은 많지 않지만 집과 가까이 있는 편의점과 같다.)_

캐시 메모리들은 CPU(코어)와 가까운 순서대로 계층을 구성한다.

- L1(Level 1) 캐시
- L2 캐시
- L3 캐시

> _(용량은 L1, L2, L3 순으로 커지고, 속도는 L3, L2, L1 순으로 빨라진다.)_

L1 캐시와 L2 캐시는 코어마다 고유한 캐시 메모리로 할당되고, L3 캐시는 열 코어가 공유하는 형태로 사용된다.

----
### 참조 지역성 원리

#### 캐시 히트(cache hit)
보조기억장치는 전원이 꺼져도 기억할 대상을 저장하고, 메모리는 실행 중인 대상을 저장한다면 캐시 메모리는 CPU가 사용할 법한 대상을 예측하여 저장한다.
이때 자주 사용될 것으로 예측한 데이터가 실제로 들어맞아 캐시 메모리 내 데이터가 CPU에서 활용될 경우를 캐시 히트라고 한다.

#### 케시 미스(cache miss)
캐시 히트와 반대로, 예측이 틀려 메모리에서 필요한 데이터를 직접 가져와야 하는 경우이다.

> **캐시 적중률(cache hit ratio) = 캐시 히트 횟수 / (케시 히트 횟수) + 캐시 미스 횟수)**

<br>

캐시 메모리는 한 가지 원칙에 따라 메모리로부터 가져올 데이터를 결정한다.
#### -> 참조 지역성의 원리(locality of reference, principle of locality)

1. CPU는 최근에 접근했던 메모리 공간에 다시 접근하려는 경향이 있다.
2. CPU는 접근한 메모리 공간 근처를 접근하려는 경향이 있다.

<br><br>

#### 공간 지역성(spatial locality)
접근한 메모리 공간 근처를 접근하려는 경향

<br><br>

###### _참고 도서: 혼자 공부하는 컴퓨터구조 + 운영체제 (한빛미디어 _ 강민철 지음)_