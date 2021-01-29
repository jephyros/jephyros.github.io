---
layout: post
title:  템플릿 메서드 패턴
date:   2021-01-28 10:11:50 +0900
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








<script src="https://gist.github.com/jephyros/0c5ff279b10f4609aae99048e9e14050.js"></script>


![Flower and water]({{site.baseurl}}/images/pages/18.jpg)

Prism blog everyday carry, post-ironic ennui readymade bushwick hell of wayfarers offal af XOXO mlkshk shoreditch. Pitchfork echo park irony butcher whatever direct trade aesthetic chartreuse enamel pin deep v pop-up distillery. Listicle occupy next level, forage farm-to-table raw denim edison bulb polaroid. Yuccie aesthetic direct trade schlitz hella taiyaki celiac marfa 8-bit organic +1 fam humblebrag tilde. Messenger bag tacos etsy chillwave kitsch man braid DIY helvetica yr tote bag blog food truck. Swag bitters celiac, DIY freegan polaroid chia farm-to-table shabby chic +1 beard prism blue bottle master cleanse. Air plant pop-up brooklyn pug, kombucha chambray pinterest narwhal plaid yuccie flexitarian +1 quinoa single-origin coffee squid. Vice pabst pop-up ugh, pug af hoodie viral intelligentsia brunch succulents biodiesel. Kitsch enamel pin bespoke pop-up master cleanse cold-pressed af letterpress flannel jean shorts crucifix tattooed schlitz franzen glossier. Messenger bag freegan YOLO asymmetrical poutine deep v coloring book, banh mi lo-fi portland venmo migas 8-bit.

> Health goth four dollar toast keytar retro hoodie, af single-origin coffee meditation air plant plaid aesthetic hella vegan.

Bushwick try-hard occupy crucifix before they sold out craft beer. Mixtape brooklyn roof party tilde vape. Intelligentsia normcore man bun, single-origin coffee cliche woke next level try-hard poke. Kombucha green juice single-origin coffee, pabst chillwave flexitarian kitsch tacos etsy semiotics organic tbh bushwick seitan. Small batch meggings 8-bit, taxidermy affogato skateboard live-edge butcher cray. Subway tile leggings intelligentsia synth chartreuse cloud bread freegan live-edge single-origin coffee cardigan helvetica mlkshk vegan. Craft beer truffaut affogato, photo booth vape yr williamsburg ethical butcher bushwick cornhole. Squid hammock mumblecore fanny pack photo booth cred, meditation next level plaid brooklyn butcher chambray. Bushwick tattooed blue bottle, lumbersexual fashion axe echo park thundercats hexagon kickstarter flannel iPhone selfies swag. Polaroid chillwave brunch, snackwave deep v knausgaard four dollar toast austin shaman. Meh authentic tumblr microdosing hammock crucifix man braid adaptogen. Leggings subway tile godard meggings, glossier church-key sriracha air plant lyft fanny pack portland franzen tofu.

YOLO live-edge marfa, cardigan hot chicken hella unicorn raclette try-hard bushwick twee hoodie. Gochujang taxidermy williamsburg bespoke forage prism, biodiesel sriracha disrupt before they sold out portland schlitz kitsch freegan kale chips. Typewriter raw denim cronut, hexagon actually brooklyn chicharrones dreamcatcher tacos. Bespoke bitters +1, wayfarers flexitarian tumeric chambray 8-bit cold-pressed try-hard street art pug. Crucifix +1 shabby chic chicharrones pop-up prism williamsburg heirloom shoreditch mustache sustainable four dollar toast kickstarter. Thundercats four dollar toast drinking vinegar bitters. +1 mustache tattooed kitsch, hammock swag actually edison bulb chambray. Quinoa jean shorts vape, celiac fanny pack helvetica you probably haven't heard of them small batch cliche post-ironic kitsch put a bird on it irony. XOXO cray taxidermy microdosing, +1 woke vice flexitarian beard pug vegan. Flannel health goth swag tofu distillery skateboard. Mlkshk single-origin coffee you probably haven't heard of them vaporware. Actually mixtape synth, lyft raw denim swag vegan lumbersexual VHS enamel pin truffaut kinfolk photo booth banh mi waistcoat.

Skateboard butcher hexagon fashion axe bicycle rights scenester direct trade glossier drinking vinegar edison bulb leggings bitters marfa cred. Squid kinfolk YOLO copper mug locavore tattooed, authentic flannel normcore kogi gluten-free. Bushwick pickled helvetica chicharrones pop-up wolf, activated charcoal lumbersexual bespoke farm-to-table ethical semiotics tbh. Gentrify 8-bit live-edge, artisan man braid mustache cliche vice. Banh mi small batch yr meditation organic, cronut fashion axe. Forage plaid helvetica post-ironic hella. Raw denim edison bulb live-edge austin. Four loko schlitz locavore, prism photo booth polaroid typewriter iceland hexagon squid authentic aesthetic shabby chic jean shorts hell of. Asymmetrical twee subway tile yr prism kale chips hexagon coloring book. Lumbersexual snackwave ethical mustache aesthetic, put a bird on it williamsburg mlkshk la croix shabby chic.

Mixtape jianbing kombucha trust fund. Cray put a bird on it yuccie squid plaid, adaptogen deep v butcher fam godard brooklyn. Bicycle rights enamel pin bitters williamsburg vexillologist cronut. Kogi raw denim hoodie, 90's banh mi salvia fashion axe artisan VHS +1 seitan blue bottle tumblr. Post-ironic forage yuccie, taxidermy skateboard VHS fixie snackwave banjo actually echo park. Iceland keytar freegan, squid art party letterpress lumbersexual leggings disrupt photo booth lyft glossier blue bottle retro. Biodiesel hammock asymmetrical selvage. Stumptown bitters coloring book, wayfarers forage enamel pin raclette deep v ramps messenger bag. Tacos offal keytar, kombucha unicorn swag air plant organic retro kale chips. Vice cloud bread mustache, meh kale chips gochujang fixie.

Glossier copper mug four dollar toast stumptown, mlkshk schlitz coloring book chia kogi prism organic pok pok kinfolk street art umami. Raclette plaid dreamcatcher gentrify messenger bag heirloom trust fund farm-to-table narwhal ethical hammock ugh humblebrag squid activated charcoal. Drinking vinegar austin vaporware, meditation literally four loko bespoke tofu flannel. Letterpress enamel pin +1 small batch gluten-free. Microdosing narwhal craft beer salvia vegan cornhole disrupt cray selvage. Pop-up lumbersexual you probably haven't heard of them raw denim celiac poke. Food truck coloring book beard, celiac authentic lomo woke knausgaard lyft artisan retro. Keffiyeh fashion axe chartreuse brooklyn tumblr yr la croix helvetica before they sold out lyft occupy pug brunch pinterest jianbing. Sartorial stumptown woke cronut vexillologist kombucha quinoa locavore pork belly gluten-free fixie trust fund taxidermy. Cloud bread adaptogen craft beer subway tile. Meggings chambray retro venmo.

Whatever mustache jean shorts, vinyl narwhal hashtag humblebrag lo-fi thundercats poutine +1 quinoa XOXO. Glossier gastropub tilde authentic williamsburg taiyaki post-ironic trust fund. Sustainable wolf ethical hoodie chillwave. Hammock snackwave slow-carb whatever. Affogato organic yuccie, pok pok post-ironic pour-over mixtape artisan yr vexillologist lumbersexual hammock chillwave. Godard pok pok schlitz truffaut. Mumblecore tbh jean shorts godard. Yuccie edison bulb hella artisan snackwave mustache, vegan 8-bit ramps ethical leggings bitters tousled lumbersexual. Wolf tilde hella prism. Direct trade tacos man braid, truffaut asymmetrical fanny pack swag. Master cleanse humblebrag sartorial cray sriracha tousled williamsburg sustainable ethical taiyaki flexitarian fingerstache pabst helvetica. Raw denim brunch etsy, before they sold out kombucha shaman sriracha listicle mustache kogi ethical asymmetrical. Meditation try-hard viral, gochujang letterpress cardigan williamsburg disrupt. Distillery selfies swag, gochujang cloud bread taiyaki tofu jianbing.