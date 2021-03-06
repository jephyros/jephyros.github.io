---
layout: post
title:  Delegation Pattern
date:   2020-02-11 23:00:00 +0900
img: 6.jpg
tags: [Design Pattern, 디자인패턴, Java,Delegation Pattern]
---
델리게이트 패턴은 객체지향 프로그래밍에서 하나의 객체가 모든 일을 처리하는 것이 아니라 처리해야 할 일 중 일부를 다른 객체에 넘기는 것을 말한다. 대리자(delegate)를 지정하여 이벤트 처리를 위임하고, 실제로 이벤트가 발생하면 위임된 대리자가 콜백 메소드를 호출해준다. 이는 효율성 관점에서 중요하다. 기능을 위임할 수 있는 객체가 있다는 것은 그만큼 직접 구현해야 하는 부분이 적다는 뜻이기 때문에 큰 규모의 프로그램을 빠르게 작성할 수 있게된다.

예를 들어, 데스크톱 프로그램에서 마우스 클릭이 특정 프로그램의 이벤트 처리 함수 onClick()으로 연결되어 원하는 내용이 실행되는 과정은  복잡하지만, 우리는 모든 과정을 직접 처리하지 않는다. 그럼에도 사용자의 클릭 이벤트가 앱에 정상으로 전달되어 의도한 메소드를 실행할 수 있는 것은 클릭 이벤트를 인식하고 프로그램에 전달해주는 위임 객체가 있기 때문이다.

> #### 마우스 클릭이 동작하는 과정
1. 마우스 버튼 클릭
2. 마우스에 연결된 시리얼 케이블이나 블루투스 통신을 통해 신호 전송
3. 전송된 신호를 RS232 통신 프로토콜을 이용해 메인보드를 거쳐 운영체제의 메시지 센터로 전달
4. 신호를 수신한 운영체제가 마우스 포인터의 화면상 좌표를 확인
5. 운영체제가 해당 좌표에서 활성화된 애플리케이션 확인
6. 델리게이트를 이용하여 클릭 신호가 애플리케이션의 이벤트 처리 함수 onClick()에 대응하였음을 애플리케이션에 알림
7. 애플리케이션이 onClick() 함수를 실행
 

iOS에서 사용되는 델리게이트 패턴도 이와 같은 개념이다. 기능을 처리할 객체를 델리게이트로 설정하고, 특정 이벤트가 발생할 때 이를 델리게이트에 의해 위임된 본래의 객체로 전달해주는 역할을 한다. iOS에서는 이러한 델리게이트 패턴을 프로토콜을 통해 구현한다.


출처 : 꼼꼼한 재은씨의 스위프트 기본편. 꼼꼼한 재은씨의 스위프트 문법편

#### <strong> 델리게이션 구조란?
델리게이션은 언어 구조라기보다는 객체가 서로 기능을 분담해서 연계하며 작동하는 전형적인 디자인 패턴이다. 객체지향에서는 보통 델리게이트(델리게이션)를 '어떤 객체가 처리할 수 없는 메시지를 받았을 때 다른 객체에 처리를 대신하게 하는 구조'라고 설명한다.

클래스 로더가 클래스 로딩을 요청받게 되면 캐시, 부모 클래스 로더, 자신 클래스 로더 순으로 클래스 로딩이 된다. 캐시에서는 클래스를 로딩한 적이 있는지 확인한다. 이전에 로딩된 클래스는 해당 클래스 로더의 캐시에 저장되고 다음 번 요청 시 캐시에 저장된 내용을 사용한다. 해당 클래스를 로딩한 적이 없다면 상위 부모 클래스 로더에게 클래스 로딩 요청을 위임한다. 클래스 로딩을 위임받은 부모 클래스 로더 또한 자신의 캐시를 먼저 확인하고 해당 클래스를 이전에 로딩한 적이 없다면 그 클래스 로더의 부모에게 클래스 로딩을 위임하는 동일한 과정을 거친다. 최상위 부트스트랩 클래스 로더까지 요청이 위임되고 이전에 클래스가 로딩된 적이 없다면 최상위 부모부터 자식 클래스 로더 순서로 클래스 로딩을 시도한다. 이러한 방식을 '델리게이션 구조'라 한다.

![Delegation Pattern]({{site.baseurl}}/images/pages/20200211/delegation_01.png)


***

#### 자바스크립트의 <strong>이벤트 델리게이션 패턴</strong>
자바스크립트에서 퍼포먼스를 높이는데 있어서 굉장히 중요한역할을 차지하고있다.
{% highlight html %}
    <div id="wapper">
        <div id="btn1"> btn1 </div>
        <div id="btn2"> btn2 </div>
        <div id="btn3"> btn3 </div>
        <div id="btn4"> btn4 </div>
        <div id="btn5"> btn5 </div>
    </div>
{% endhighlight js %}    
예들들어 위와 같은 구조에서 버튼 1~5 까지 이벤트 리스너를 줄 경우 아래처럼 각 버튼마다 주는 방법이있다.
{% highlight js %}
    document.getElmentById('btn1').addEventListener('click',funciton(){
        console.log('btn1 click')
    });
    document.getElmentById('btn2').addEventListener('click',funciton(){
        console.log('btn2 click')
    });
    ....    
{% endhighlight js %}    
하지만 이런 DOM Element가 많아지거나 DOM Element가 동적으로 변하는 상황이라면 위와같이 하나하나 리스너를 등록하는 방식은 브라우저의 메모리 부족과 낮은 퍼포먼스를 야기하게 될 것이다. 
이를 해결하기위해 권장하는 패턴이 바로 이벤트 델리게이션 패턴이다.
즉, 버튼에 개별적으로 이벤트 리스너를 등록하지 말고, 그 버튼을 감싸고 있는 Parent Wrapper Div 에 이벤트 리스너를 등록하여, 그 이벤트의 Target 값을 이용해 해당 버튼의 클릭 이벤트를 핸들링하는 것이다.
{% highlight js %}
    document.getElementByid('wrapper').addEventListerner('click',function(e){
        var target = e.target || e.srcElement;
        switch(target.id){
            case 'btn1':
                console.log('btn1 click);
                break;
            case 'btn2':
                console.log('btn2 click);
                break;
            ...

            default:
                break;
        
        }
        e.stopPropagation();
    },true )
{% endhighlight js %}    
이벤트 델리게이션 패턴을 사용하면 위와 같이 변경될 수 있다.

자바스크립트의 표준 문서에 있는 이벤트 전달 및 처리단계는 다음과 같고 이러한 단계를 알고있다면 이벤트 델리게이션 패턴을 좀더 쉽게 이해할 수 있다. 
* 캡처링 단계 (Event Capturing)
* 대상 단계 (Event Target)
* 버블링 단계(Event Bubbling)

자세한 내용은 찾아보자.
