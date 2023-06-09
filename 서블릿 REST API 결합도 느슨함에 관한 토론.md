# 서블릿 엄격함, restAPI 느슨함, 결합도가 낮다. 의 의미들 정리

<aside>
💡 질문 : REST API는 클라이언트와 서버 간의 결합도를 낮추어 유연성을 높이고, 서비스 확장성을 개선할 수 있다고 하는데 여기서 결합도가 낮다는게 무슨 의미야?

</aside>

대답 : REST API에서는 클라이언트와 서버 간의 인터페이스를 통해 상호작용하기 때문에, 클라이언트와 서버 간의 결합도가 낮아지게 됩니다. 즉, 서로 다른 플랫폼에서도 같은 인터페이스를 공유함으로써 서로 상호작용할 수 있기 때문에, 클라이언트와 서버 간의 구현 방식이 서로 독립적으로 변화하더라도 상호작용하는 데 문제가 없습니다. 이러한 구조는 유연성을 높여 서비스 확장성을 개선할 수 있게 해줍니다.

해석 : 

결합도가 낮다 의 의미

- 결합도가 낮다는 것은 의존성이 낮다는 것이다.
- 의존성이 낮다는 것은 서로 독립적이라는 뜻이다.
- 즉 클라이언트와 서버가 독립적이라는 의미이다.
    - rest API는 클라이언트와 서버간 통신할 때 데이터만 주고 받음
    - 그래서 클라이언트의 브라우저가 크롬, 엣지, 안드로이드 등 다르더라도 알맞은 데이터만 보내주면 서버 하나로 여러 플랫폼에서 동작시킬 수 있음
    - 그래서 유연성이 높아지고 서비스 확장성이 높아지는 것임

대답 : 반면에, 기존의 웹 애플리케이션에서는 서버 측에서 HTML 페이지를 동적으로 생성하여 클라이언트에게 전송하는 방식으로 동작하였기 때문에, 클라이언트와 서버 간의 결합도가 높았습니다. 이러한 구조는 클라이언트와 서버 간의 구현 방식이 서로 의존하게 됨으로써 서비스 확장성을 제한하고, 유지보수를 어렵게 만들어버리는 문제점이 있습니다.

해석 : 

- jsp/servlet 으로 만든 웹 서비스는 SSR(서버 사이드 랜더링)으로 동작함
- 클라이언트에서 요청을 보내면 서버에서 해당 요청을 받고 요청을 토대로 html을 만들어서 클라이언트로 보내줌
- 여기서 부터 뇌피셜 :
    - 서버는 html을 만들어서 클라에게 보내줌
    - 브라우저의 종류에 맞게 html 을 만들어서 보내줘야함
    - 대표적으로 안드로이드는 html 받지 못함
    - 그래서 서버와 클라이언트가 독립적이지 않다고 할 수 있고
    - 결과적으로 결합도가 높고 의존성이 높고 확장성이 제한적이다.
- 즉 서버와 클라이언트가 독립적이지 않음

결론 : restAPI로 통신하면 느슨한거고 서블릿을 이용하면 엄격한거다.

<aside>
💡 스프링이 서블릿 기반인 이유

</aside>

뇌피셜 2

- 스프링이 서블릿 기반인 이유
- 클라이언트의 요청을 동적으로 처리하기위해 처음 만들어진게 서블릿임
    - 서블릿 : java코드 내에 html 삽입하는 방식
- 서블릿으로 html 만들어내는게 힘들어서 발전된 게 jsp임
    - jsp : html 내에 java 코드 넣는 방식
        - jsp 동작 방식은 jsp페이지를 서블릿 컨테이너가 해석해서 결과적으로 서블릿을 만들어주는 방향으로 동작함.
- jsp/서블릿을 발전시킨게 spring 임
    - 그래서 spring도 서블릿 기반이지 않을까 유추됨.

이제이비
