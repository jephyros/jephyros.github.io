---
layout: post
title:  Delegation Pattern
date:   2020-02-11 23:00:00 +0900
img: 6.jpg
tags: [Design Pattern, 디자인패턴, Java,Delegation Pattern]
---
델리게이션 패턴이란 하나의 객체가 다른 객체를 대신해 동작 또는 조정할 수 있는 기능을 제공 한다. 델리게이션 디자인 패턴은 Foundation, UIKit, AppKit 그리고 Cocoa Touch 등 애플의 프레임워크에서 광범위하게 활용하고 있으며 주로 프레임워크 객체가 위임을 요청 하고 (주로 애플리케이션 프로그래머가 작성하는)커스텀 컨트롤러 객체가 위임을 받아 특정 이벤트에 대한 기능을 구현 한다. 델리게이션 디자인 패턴은 커스텀 컨트롤러에서 세부 동작을 구현함으로써 동일한 동작에 대해 다양한 대응을 할 수 있게 해준다


##### 자바스크립트의 이벤트 델리게이션 패턴
자바스크립트에서 퍼포먼스를 높이는데 있어서 굉장히 중요한역할을 차지하고있다.
예들들어
{% highlight html %}
    <div id="wapper">
        <div id="btn1"> btn1 </div>
        <div id="btn2"> btn2 </div>
        <div id="btn3"> btn3 </div>
        <div id="btn4"> btn4 </div>
        <div id="btn5"> btn5 </div>
    </div>
{% endhighlight js %}    
위와 같은 구조에서 버튼 1~5 까지 이벤트 리스너를 줄 경우 각 버튼마다 줄수있다.
{% highlight js %}
    document.getElmentById('btn1').addEventListener('click',funciton(){
        console.log('btn1 click')
    });
    document.getElmentById('btn2').addEventListener('click',funciton(){
        console.log('btn2 click')
    });
    ....    
{% endhighlight js %}    
이런 DOM Element가 많아지거나 DOM Element가 동적으로 변하는 상활이라면 이런식으로 일일이 리스너를 등록하는 방식은 브라우저의 메로리 부족과 낮은 퍼포먼스를 야기하게 될 것이다. 
이를 해결하기위해 권장하는 패턴이 바로 이벤트 델리게이션 패턴이다.
즉, 버튼에 일일이 이벤트 리스너를 등록하지 말고, 그번튼을 감사고 있는 Parent Wrapper Div 에 이벤트리스너를 등록해서, 그 이벤트의 target값을 이용해서 해당 버튼의 클릭 이벤트를 핸들하는 것이다.

위의 이벤트는 아래와 같은 코드로 변경될수있다.
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








https://yeoulcoding.tistory.com/142

...블라블라



