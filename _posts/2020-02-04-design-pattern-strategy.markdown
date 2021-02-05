---
layout: post
title:  전략 패턴
date:   2020-01-28 10:11:50 +0900
img: 5.jpg
tags: [Design Pattern, 디자인패턴, Java,Strategy Pattern]
---
전략 패턴(Strategy Pattern)이란 "실행 중에 알고리즘을 선택할 수 있게 하는 행위 소프트웨어 디자인 패턴이다" 라고 위키백과에서 정의하고있다.
> * 특정한 계열의 알고리즘들을 정의하고
> * 각 알고리즘을 캡슐화하며
> * 이 알고리즘들을 해당 계열 안에서 상호 교체가 가능하게 만든다.

이 전략 패턴은 우리가 많이 사용하는 서비스 레이어구현시 Service 인터페이스를 만들고 ServiceImpl 구현체를 만들고 다음과 같이 사용한다.
알고리즘(로직)이 변경 또는 추가되어서 적용해야된다면 ServiceNewImpl 로 구현 하면된다. 물론 스프링에서는 여러 구현체가 존재할 경우 주입대상을 명확히 하기위해 @Qualifier 같은 어노네이션을 사용한다. 
{% highlight js %}
    @Autowired
    private Service service;
    또는
    private final Service service;
    public 생성자(Service service){
        this.service =service;
    }
{% endhighlight js %}    
논외의 이야기지만 이러한 Service 구현체가 1개 일경우에도 이렇게 구현하는것을 불필요하다는 갑론을박도 많다. 나 또한 서비스구현체가 1개로 변동될 일이 없다면 마치 습관처럼 인터페이스를 만들고 구현체를 별도로 만드는것은 불필요한 일이라 생각된다.

아래 그림은 전략 패턴에 대한 UML이다. 
![Strategy design pattern.]({{site.baseurl}}/images/pages/20200204/strategy_01.jpg)

< 출처:위키백과(https://ko.wikipedia.org) >


##### <strong> 전략 패턴 vs 템플릿 메서드 패턴
잘 살펴 보면 전략패턴과 템플릿 메서드 패턴은 패턴의 목적은 같고 구현방법의 차이만 존재한다고 생각된다.

<table>
  <tr><th>디자인 패턴</th><th>목적</th><th>구현방법</th></tr>
  <tr><td>전략 패턴</td><td>행위의 확장</td><td>구성(구현과 인터페이스 분리)</td></tr>
  <tr><td>템플릿 메서드 패턴</td><td>행위의 확장</td><td>상속(구현과 인터페이스 함께 있음)</td></tr>  
</table>
   위 설명중 "인터페이스"는 자바의 인터페이스 코드를 의미하는 것이 아닌 좀더 큰 의미의 규약,약속을 의미한다.

***

##### 그럼 행위를 확장 할때 전략 패턴과 템플릿 메서드 패턴중 어느것을 써야될까? 
그때 그때 상황에 따라 다르겠지만 어느 것을 사용해도 괜찮다면 아래 원칙에 따라
> 상속보다 구성이 더나은 방법이다 - 디자인패턴원칙중

구현과 인터페이스를 분리하는 것이 낫다.




