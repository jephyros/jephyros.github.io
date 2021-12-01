---
layout: post
title:  C#, cefSharp , Web 기반 POS구축
date:   2021-11-21 21:00:00 +0900
img: 3.jpg
tags: [c#, cefSharp]
---
c# 과 cefSharp를 사용하여 웹기반 POS시스템을 개발 중 듀얼스크린을 통해 고객동의 사인을 받는 기능을 구현해야했다. (c#의 winform 을 사용하여 구현함.)

이를 위해서는 두가지 문제에 대한 해결책이 필요하다
> <Strong>첫째, 듀얼스크린모니터에 원하는 웹페이지를 로드 하는방법</strong>

###### Screen객체를 통해 모든 스크린의 정보를 획득한 후 메인창이 실행되지않는 Screen 위치(배열)를 찾은 후 두번째 Form2의 Location에 지정한다. 이렇게 면 두번째 창에 Form2를 실행키실 수있다.

{% highlight c# %}
Screen[] screens = Screen.AllScreens;
    
if(screens.Length>1)
{
    Screen scrn = (screens[0].WorkingArea.Contains(this.Location)) ? screens[1] : screens[0];
    secondForm = new Form2(this);
    secondForm.Show();
    secondForm.Location = new System.Drawing.Point(scrn.Bounds.Left, 0);
    secondForm.WindowState = FormWindowState.Maximized;

}
{% endhighlight %}

###### Form2 에서 cefSharp를 로드시며놓는다. Form2_Load 이벤트에서 아래처럼 지정한다. new ChromiumWebBrowser() 을 Form2 생성자에 위치시키면 <strong>secondChrome.JavascriptObjectRepository.Settings.LegacyBindingEnabled = true;</strong>부분에서 값을 변경할수 없다는 에러가 발생 한다.

{% highlight c# %}
private void Form2_Load(object sender, EventArgs e)
{
    String secondURL = "file:///C:/project/htmltest/advertise.html";            
    secondChrome = new ChromiumWebBrowser(secondURL);
    secondChrome.Dock = DockStyle.Fill;// From창에 ChrominumWebCrowser 가득 채우기
    // Javascript Event 호출 활성화 
    secondChrome.JavascriptObjectRepository.Settings.LegacyBindingEnabled = true;
    secondChrome.JavascriptObjectRepository.Register("secondcAPI",
                new SecondChromeAPI(parentForm), false, BindingOptions.DefaultBinder);
    this.Controls.Add(secondChrome);  

}
{% endhighlight %}

> <Strong>둘째, 웹페이지에서 Javascript 로 c# 의 함수를 호출하여 제어 하는 방법</Strong>

###### Form 이 로드될 경우 아래처럼 Javascript Event 호출을 활성화 하고 웹페이지에서 호출할 객체명(cAPI)을 등록해준다.

{% highlight c# %}
// c# Form initialize 부분
chrome.JavascriptObjectRepository.Settings.LegacyBindingEnabled = true;                
chrome.JavascriptObjectRepository.Register("cAPI", new SignAPI(secondForm), false, BindingOptions.DefaultBinder);
{% endhighlight %}

###### internal Class로  아래처럼 호출하는 Class를 구성한다. 아래 예제는 두번째창을 제어하기 위해 Form2객체를 선언했으며 생서자를 통해 객체를 참조 받아서 내부 함수에서 호출 할 수 있도록 하였다.
{% highlight c# %}
internal class SignAPI 
{
    Form2 secondForm;
    public ChromeAPI(Form2 secondForm)               
    {
        this.secondForm = secondForm;
    }    
    public Boolean approvalCall(string url )
    {
        secondForm.secondChrome.Load(url);        
        return true;
    } 
}
{% endhighlight %}

###### 최종적으로 웹페이지에서는 아래처럼 호출 할 수있다.
{% highlight js %}
// call.html 의 javascript
function callTest(){

    cAPI.approvalCall('전달하고자하는 파라메타');
    
}
{% endhighlight %}


