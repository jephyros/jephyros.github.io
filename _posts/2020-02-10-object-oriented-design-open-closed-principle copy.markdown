---
layout: post
title:  개방 폐쇄의 원칙
date:   2020-02-10 18:10:00 +0900
img: 2.jpg
tags: [Object Oriented Design, 객체지향설계, Java,Open-Closed Principle]
---
개방-폐쇄 원칙(Open-Closed Principle)이란 "소프트웨어 개체(클래스, 모듈, 함수 등등)는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야 한다"는 프로그래밍 원칙이다.

##### 그럼 확장은 무엇이고 수정은 무엇인가?
* 확장은 새로운 타입을 추가함으로써 새로운 기능을 추가 할 수 있다.    
* 수정은 확장이 일어날때 상위레벨 이 영향을 받지 않는다. 이를 위해 Abstraction 과 Inversion 을 가지고 상위레벨이 하위레벨의 의존성을 제거한다. 

![example]({{site.baseurl}}/images/pages/20200210/openclose_01.png) 

왼쪽 그림의 경우 Copy 에 Keyboard 외에 추가로 PunchReader 가 필요하다면 Copy 클래스가 수정되어야한다.
그러나 오른쪽 그림의 경우 Interface 로 의존성을 역전시키면 Copy클래스의 수정이 없이도 PunchReader 기능을 추가할 수 있게 된다.

![code]({{site.baseurl}}/images/pages/20200210/openclose_02.png)

이렇게 되면 Copy라는 클래스는 수정에는 닫혀있고 확장에는 열려있는 상태가 된다.

[OCP 해결하는 단계 예제 https://github.com/msbaek/expense](https://github.com/msbaek/expense)

< 출처:백명석님의 클린코더스 강의 >


> 새로운 타입이 추가되는 환경에서는 OOP가 맞지만 기능만 계속 추가 될 경우 OOP보다는 Functional(Structured) Language 가 더 맞을 수 도 있다.



##### <strong> 소프트웨어(어플리케이션)의 두가지 가치 (Two Values of SW)
만일 소프트웨어가 버그도 업고, 성능 이슈도 없는 상태로 최초 개발되면 그 가치는 매우 높다. 이러한 가치는 사용자의 현재 요구를 만족시킬때 달성된다. 하지만 사용자의 요구는 시대변화와 트렌드에 맞추어 계속 변화한다. 이러한 변화는 소프트웨어의 가치를 낮추게 된다. 이런 지속적인 변화를 용인하고, 촉진 할 수 있는 소프트웨어가 되어야 그 가치에 도달 할 수 있다. 
처음에는 가치가 높았지만 높은 경직성을 갖는 소프트웨어는 수정이 어렵고 결과적으로 사용자들은 좋아하지 않고, 수익율도 떨어질 것이다.
반대로 처음에는 가치가 낮았을지라도 낮은 경직성을 갖는 소트트웨어의 수정에 쉽다면, 수익성은 올라가고 사용자들은 점점더 좋아할 것이다.
극단적인 예가 될수있지만 소프트웨어의 경직성을 표현하기에는 적당할 것이다. 정리하면 다음과 같다.

<strong>Secondary Value of SW is it's behavor </strong> - 일반적으로 우리가 생각하는 SW의 가치
* 현재의 SW가 현재 사용자의 현재 요구사항을 만족하는가?

<strong>Primary Value of SW </strong> 
* 지속적으로 변화하는 요구사항을 수용(tolerate,facilitate) 하는 것.
* 대부분의 SW의 경우 현재의 요구사항을 잘 만족하지만 변경하기는 어렶다.



***
이 경직성을 낮추는 원칙 중 하나가 개방-폐쇄의 원칙이다. 하지만 너무 이러한 원칙을 따르면 그만큼 소프트웨어는 복잡해질수 밖에 없다.
즉, 복잡성과 경직성은 trade-off 관계임을 명심하자. 개방-폐쇄 원칙은 <strong>Silver Bullet</strong>이 아니다.


***
#### 개방-폐쇄의 원칙을 어기면 코드에 나타나는 현상 
 - Enum 값을 Switch 나 if 문으로 반복적으로 판단하고있다.
 - Enum 추가는 쉽지만 모든 코드의 Switch ,if 문을 수정해줘야함.

***
#### 그럼 언제사용할것인가?
 - 타입이 많고 추가될가능성이 많다.
 - 타입의 멤버로 분기처리되는 코드 가 매우 많다.

