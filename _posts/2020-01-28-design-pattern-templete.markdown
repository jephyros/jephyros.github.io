---
layout: post
title:  템플릿 메서드 패턴
date:   2020-01-28 10:11:50 +0900
img: 8.jpg
tags: [Design Pattern, 디자인패턴, Java,Template Method Pattern]
---
템플릿 메서드 패턴이란 "소프트웨어 공학에서 동작 상의 알고리즘의 프로그램 뼈대를 정의하는 행위 디자인 패턴이다. 알고리즘의 구조를 변경하지 않고 알고리즘의 특정 단계들을 다시 정의할 수 있게 해준다." 라고 위키백과에서 정의하고있다.
##### 좀더 개발자스럽게 표현한다면 다음과 같다. 
* 메소드에서 알고리즘의 골격을 정의한다.
* 알고리즘의 여러 단계 중, 일부는 서브클래스에서 구현할 수 있다.
* 알고리즘의 구조는 그대로 유지하면서 서브클래스에서 특정 단계를 재정의 할 수 있다.

자바를 공부하면 누구나 배우는 추상클래스를 가지고 클래스의 상속, 오버라이드등의 기본기능을 좀더 고급스럽게 사용한다는 느낌이다.

내가 처음 템플릿 메서드 패턴을 접한것은 어느 책인지는 기억이 잘 안나지만 내용은 JDBC를 통해 SQL에 접속하여 데이터를 가저오는 코드를 리팩토링하는 과정에서 이러한 중복 코드를 템플릿 메서드 패턴을 사용하여 리팩토링 한다는 내용이였다.


아래 그림은 템플릿 메서드 패턴에대한 UML이다. 
![Template Method design pattern.]({{site.baseurl}}/images/pages/20200128/templatemethodpattern_01.jpg)

< 출처:위키백과(https://ko.wikipedia.org) >

내용은 간단하다. 추상클래스에 는 3개의 메서드가 존재하는데 상속가능한 primitive1(), primitive2() 2개의 메서드와 상속 불가한 templateMethod()가 존재한다.
templageMethod()메서드는 primitive1(),primitive2() 를 사용해서 알고리즘(수행순서,제약 등.) 이 정의되어있고 이 알고리즘은 변하지않고 primitive1(),primitive2()는 구현 하는 서브클래스에 맞겨놓는 방식이다. 그렇지만 너무 이 내용에 집착(?)하면 명확한 알고리즘 순서가 있을때 템플릿 메소드 패턴을 사용한다고 오해(제한) 할 수 있음을 주의하라는 글을 본적있다.
즉, <strong> 단지 관심사를 분리하거나 코드중복을 줄이거나 혹은 전 처리나 후 처리등을 위해서 사용하는 경우도 많이 볼 수 있다.</strong>
또한, 처리흐름이 있더라도 처리흐름을 따로 분리해서 메서드를 만드는 경우도 많지 않다.
예를 들어 스프링의 AbstractHandlerMethodExceptionResolver 의 doResolveException 메서드에서 doResolveHandlerMethodException 추상메서드를 호출하는데 호출하는이유가 단지 형변한을 위한 전처리를 작업을 위해 템플릿 메서드 패턴을 사용했다.

#### 템플릿 메서드 패턴 설명에 나오는 전형적인 예시들.
##### 차끓이기 
1. 물을 붓는다.
2. 물을 끓인다.
3. ...

##### 로그인 처리
1. 보안처리
2. 인증처리 
3. ...

##### 추상소켓버서
1. 서버를 뛰운다.
2. 접속을 대기한다.
3. 입력을 받는다.
4. ...


##### <Strong> 그럼 템플릿 메서드 패턴은 스프리의 어디에서 어떻게 사용되고있는지 좀더 찾아보자</Strong>
* java.io.InputStream 의 read() 메서드
{% highlight js %}
    public abstract int read() throws IOException;  // 서브클래스에 구현 위임 
    // BufferedInputStream, ByteArrayInputStream 등의 다양한 클래스에 구현되어있다.
    
    public int read(byte b[], int off, int len) throws IOException {
        Objects.checkFromIndexSize(off, len, b.length);
        if (len == 0) {
            return 0;
        }
        int c = read();  //read() 호출부
        if (c == -1) {
            return -1;
        }
        b[off] = (byte)c;

        int i = 1;
        try {
            for (; i < len ; i++) {
                c = read(); //read() 호출부
                if (c == -1) {
                    break;
                }
                b[off + i] = (byte)c;
            }
        } catch (IOException ee) {
        }
        return i;
    }  
{% endhighlight %}
* java.util.Collections의 sort() - 추상클래스가 아닌 Interface 의 Default Method 방식
{% highlight js %}
    public static <T> void sort(List<T> list, Comparator<? super T> c) {
        list.sort(c);
    }

    //List 인터페이스의 default Method 는 listIterator() 를 호출함
    // 이부 분은 다른 구현클래스(ex. ArraysList 등 )에서 정의됨
    public interface List<E> extends Collection<E> {
        .....
        default void sort(Comparator<? super E> c) {
            Object[] a = this.toArray();
            Arrays.sort(a, (Comparator) c);
            ListIterator<E> i = this.listIterator();
            //listIterator 를 호출함
            for (Object e : a) {
                i.next();
                i.set((E) e);
            }
        }
        .....
    }
{% endhighlight %}




