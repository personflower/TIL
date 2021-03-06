# C# Web 프로그래밍
#### Web Server 프로그래밍 
- 아무래도 나는 .NET 개발자이기에 Web 개발도 ASP.NET으로 하고 있다. &#128557;

- ASP.NET이라는 Web Framework를 활용

##### ASP.NET의 종류
>1. 기존 Winform 프로그래밍 방식을 Web에 적용한 ASP.NET WebForms
>1. UI, Model 그리고 Controller를 분리한 ASP.NET MVC (MVC 5)
>1. REST API 개발을 쉽게 해주는 ASP.NET Web API

##### ASP.NET Core
- ASP.NET Core라는 명칭으로 새로운 Architecture로 크게 변화

- ASP.NET Core = ASP.NET MVC6, Entity Framework Core를 지원 + WebForms 제거 + Web API를 MVC에 통합

- ASP.NET Core는 가장 기본적인 기능을 제외하고 모두 Optional<br>
개발자가 필요한 기능들을 별도로 추가해서 사용

#### Web API를 사용하는 Client 프로그래밍
- C#으로 Web 리소스를 다운로드하거나 Web API를 호출하기 위해 여러 .NET Library를 사용할 수 있음
>1. WebClient
>1. HttpWebRequest / HttpWebResponse