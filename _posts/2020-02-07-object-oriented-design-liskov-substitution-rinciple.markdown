---
layout: post
title:  리스코프 치환 원칙
date:   2020-02-07 10:11:50 +0900
img: 3.jpg
tags: [Object Oriented Design, 객체지향설계, Java,Liskov Substitution Principle]
---
 리스코프 치환 원칙(Liskov Substitution Principle)이란 "자료형 <strong>S</strong>가 자료형 <strong>T</strong>의 하위형이라면 필요한 프로그램의 속성(정확성, 수행하는 업무 등)의 변경 없이 자료형 <strong>T</strong>의 객체를 자료형 <strong>S</strong>의 객체로 교체(치환)할 수 있어야 한다"를 만족해야한다.

 >What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T." - BarbaraLiskov, Data Abstraction and Hierarchy, SIGPLAN Notices, 23,5 (May, 1988).

좀더 쉽게 표현해보면 

>상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.


##### 리스코프 치환 원칙을 위반하면?
 * 모든 클래스에서 하위클래스를 명시적으로 지정해서 코드해야함.
 * 결과적으로 OCP(개방 폐쇄 원칙)를 사용할 수 없게됨.
 * 코드가 복잡해짐.
 * 상위(부모) 클래스가 하위(자식)클래스가 어떻게 구현되어있는지 알아야 되는 불상사가 생김.

##### 리스코프 치환 원칙을 잘 지키면?
 * 상위클래스를기준으로 작성된 코드가 문제없이동작한다.
 * 추상화된 인터페이스 하나로 공통의 코드를 작성할수 있다.

로버트 마틴(로버트 C. 마틴 Liskov Substitution Principle)은 LSP를 다음과 같이 소개 하고 있습니다.
> 개방 폐쇄 원칙 OCP 은 관리가능하고 maintainable, 재사용 reusable 가능한 코드를 만드는 기반이다. 잘 설계된 코드는 기존 코드의 변경 없이 확장 가능하다. OCP 를 가능케 하는 중요 메커니즘은 추상화와 다형성이다. 추상화와 다형성을 가능케 하는 키 메커니즘이 상속이다. 추상 기반 클래스의 순수 가상 함수로 부터 클래스를 상속 파생 시킴으로써 추상화된 다형 인터페이스를 만들어 낼 수 있다.

즉, 리스코프 치환원칙(LSP)은 바로 상속의 룰 이며, 최고의 상속 구조 특성을 갖추게 하며, 개방폐쇄원칙(OCP)을 위반하지 않도록 인도하는 원칙 이라고 말하고 있습니다.  

리스코프 치환원칙을 설명할 때 가장 많이 사용되는 예시가 정사각형과 직사각형의 관계에 대한부분이다. 언듯 둘 사이의 관계를 상속관계로 풀 수 있을 것이라 생각 할 수 있지만 SOLID법칙의 기준으로 본다면 코드상으로 <strong> 둘 사이는 상속 관계로 존재할수 없다.</strong> 가로 세로 길이에대한 정의가 상충되기 대문에 한쪽방향으로 상속을 하면 부모클래스의 속성을 위반할 수밖에 없다.
