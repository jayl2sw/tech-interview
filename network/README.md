# Network

> **네트워크**는 컴퓨터와 기타 장치들이 상호 연결되어 데이터를 주고받을 수 있는 시스템을 의미합니다. 이러한 시스템을 통해 사용자들은 데이터를 공유하고 통신할 수 있으며, 이를 통해 다양한 서비스를 제공하고 활용할 수 있습니다.



### 1. www.naver.com

* www.naver.com을 브라우저에 입력하고 접속을 시도 했을 때, 네트워크 상 어떤 일이 일어나는 지 최대한 자세하게 설명해주세요.

### 2. CORS

* CORS란 무엇이고 왜 사용하나요?
* CORS error를 해결 할 수 있는 방법 3가지에대해 설명해주세요.

* CORS(Cross-Origin Resource Sharing)는 웹 애플리케이션에서 다른 도메인(Origin) 간에 리소스를 공유할 수 있도록 하는 보안 메커니즘입니다. 기본적으로 브라우저는 보안 상의 이유로 동일 출처 정책(Same-Origin Policy)를 따르는데, 이는 웹 페이지에서 리소스를 요청할 때 해당 리소스의 출처가 동일해야만 요청을 허용한다는 것을 의미합니다. CORS는 이러한 동일 출처 정책을 우회하여 다른 도메인 간에 리소스를 공유할 수 있도록 해줍니다.

> 1. 서버 측에서 CORS 헤더 추가: 서버 측에서 응답에 CORS 관련 헤더를 추가하여 브라우저에게 리소스 공유를 허용하는 것입니다. 이 헤더에는 "Access-Control-Allow-Origin"과 "Access-Control-Allow-Methods" 등이 포함될 수 있으며, 허용할 도메인과 허용할 HTTP 메서드를 명시합니다.
> 2. 프록시 서버 사용: 동일 출처 정책을 적용받지 않는 중간 서버(프록시 서버)를 사용하여 CORS 문제를 우회하는 방법입니다. 클라이언트는 프록시 서버에 요청을 보내고, 프록시 서버는 해당 요청을 원격 서버로 전달하고 응답을 클라이언트에게 다시 전달합니다. 이를 통해 브라우저는 동일 출처 정책을 적용받는 것이 아니기 때문에 CORS 문제를 회피할 수 있습니다.
> 3. JSONP 사용: JSONP(JSON with Padding)는 동일 출처 정책을 우회하는 또 다른 방법입니다. 서버는 JSON 데이터를 콜백 함수로 감싼 형태로 응답을 반환하고, 클라이언트는 스크립트 태그를 사용하여 해당 응답을 가져옵니다. 이를 통해 클라이언트는 스크립트 실행에 대한 동일 출처 제한을 우회할 수 있습니다.
