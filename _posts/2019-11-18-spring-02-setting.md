**생성된 pom.xml의 기본 내용**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 150936_pom_xml.png">

**JRE System Library**

<center><img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 231427_jrever.png" /></center>
<p>Java 개발, 실행하는데 필요한 라이브러리.
기본값으로 [J2SE-1.5]로 잡혀있다.</p>

**JRE System Library 변경**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 231950_javase8.png" />

1.8 버전으로 변경해준다.

**Annotation 사용해보기**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 232419_controller.png">

아직 dependency를 주입하지 않았기 때문에 사용할 수 있는 어노테이션이 없다.
spring-web 의존성이 필요하다

**spring-web 의존성 주입**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 233554_web+springelements.png">

pom.xml에 spring-web dependency를 주입한다.
Project Explorer에 [Spring Elements]가 생겼다.

**다시 Annotation 사용해보기**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 233736_usingannotation.png">
맞는놈으로 골라서 import 하자

**Build Path의 Server Runtime에 라이브러리 추가하기**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 234122_buildpath.png" />

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 234413_buildpathlib.png">

tomcat 라이브러리는 잠시 후에 Server로 구동하려고 할때 친절하게 등록하는화면을 보여준다. 그런데도 굳이 이 과정을 넣어두는 이유는
나중에 나는 분명히 잘못이 없는데 서버 관련 클래스를 로딩하지못했다 라는 에러를 만날텐데 그 때 이 라이브러리를 지우고 다시 등록해주는것으로 해결이 될 때가 있기 때문이다.

**Run on Server...?**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 235250_serverrun.png">

tomcat으로 구동하고 싶은데 메뉴가 안보인다

**패키징 형태를 war로 변경**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 000246_onlywar.png">

tomcat 서버에 파일을 올리려면 jar가 아닌 war 형식으로 배포를 해야하는데, 첫 프로젝트 생성시 packaging 설정을 jar 인 상태로 생성하였기 때문에 war로 바꾸어 주어야 한다. pom.xml에 따로 명시해두지 않으면 default로 jar이다.

**Project Explorer 변경됨**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-14 235921_menuchanged.png">

배포형태를 .war로 하겠다고 한것 만으로 보여지는 메뉴가 달라졌다

**Run on Server!**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 000410_server.png">

이제 Run on Server 메뉴가 보인다.

**패키징 태그 에러**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 000620_webxmlerror.png">

위에서 추가한 package 태그에서 에러가 났다.
web.xml 파일이 없단다.

**[web.xml] 생성**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 001249_creatxml1.png">

위치가 중요하다. src\main\webapp\WEB-INF 폴더에 추가해야한다.

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 001423_createxml2.png">

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 001630_createxml3.png">

**[applicationContext.xml] 추가**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 003017_createapplicationcontext.png">

위와 같은 .xml이지만 용도가 다르다. Bean 추가용으로 생성할 xml 파일을 편하게 만들수 있다.

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 003114_createapplicationcontext2.png">

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 003317_createapplicationcontext3.png">

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 003650_createappllicationcontext4.png">

**[*-servlet.xml] 추가**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 004022_createservletxml.png">

생성시 spring-servlet.xml으로 했는데,
아무 설정도 하지 않을 시 아래의 selvelt-name에 맞춰서 파일을 생성해야 한다. 다른 태그를 추가하여 상관관계만 명시해주면 이름이 달라도 문제없다.

<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 004433_createservletxml2.png">

**그냥 넘어갈리가 없다**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 005956_error.png">

**dependency 추가**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 010100_errorfix.png">

spring-webmvc는 spring-core, spring-context, spring-web, spring-aop, spring-beans, spring-expression 에 대해 의존성이 있으므로 spring-webmvc하나로 5가지 의존성을 주입할 수 있다.
applicationContext.xml, spring-servlet.xml에 mvc기능을 나중에 따로 추가해야겠다. 파일 만들기전에 그냥 webmvc로 추가할 걸 그랬다.

**다시 Run on Server**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-15 010350_hello.png">

잘 뜬다.
ResponseBody로 return값을 직접출력했다.
아직 view(jsp)는 만들지 않았다.

**추가한 내용**
<img src="{{ site.url }}/assets\image\spring\02-setting\2019-11-17 193320_nomappingerror.png">

잘 되더니 다음날 에러가 떴다. 연결한 url이 없단다. HomeController.java에 RequestMapping 다 해놨는데.
그냥 bean을 직접 명시해서 이클립스 입에 처넣어주었다.
어차피 추가할 코드 미리 추가했다 치고 넘어가자.
스프링은 에러와의 싸움이다.
