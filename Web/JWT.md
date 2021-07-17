# JWT에 대한 이해

<br>

## 목차
#### 1. Session 인증
- Session 인증?
- Swssion 인증의 장단점

#### 2. JWT 인증
- JWT?
- JWT 구조
- JWT 인증의 장단점
- Refresh Token?
- Access Token의 보안
- JWT 주의사항

#### 3. 참고자료

<br>

## Session 인증

#### 1. Session 인증?
- Server Side Rendering, Server Session을 사용한 인증.
- Server Session을 모두 Server Memory에 저장된다. 따라서 확장 시 모든 Server가 접근할 수 있는 중앙 세션 관리 시스템이 필요한다.
- 주로 규모 확장 계획이 없거나, 소규모 프로젝트에서 사용한다.

#### 2. Session 인증의 장단점
|Pros|Cons|
|----|----|
|Server에서 사용자 요그인 확인이 쉽다.|Session을 Server Memory에 저장하면 부하가 생길 수 있다.|
|Client의 변화에 영향을 덜 받는다.|Cookie는 단일 Domain이기 때문에 여러 Domain일 경우 추가 관리가 필요하다.|
|Server와 Client 간의 주고받는 데이터가 작다.(JWT와 다르게 Signiture와 같은 추가 정보가 없다.)||


## JWT 인증

#### 1. JWT?
    Json: 표현법
    Web: 사용처
    Token: 인증서
- JWT는 Web에서 사용하는 Json으로 표현된 인증서이다.
- JWT 인증은 token 기반의 사용자 인증 방식으로, session 인증과는 다르게 client에 session을 저장하는 방식이다.
- 필요 정보를 token의 payload(body)에 저장한다.
- SPA(Single Page Application)에서 주로 쓰이는 인증 방식이다.
- 인증받은 사용자에게 token을 발급한 후, 이루 client에서 server에 요청할 때 token을 함께 보내 인증을 한다.
- Session을 사용하는 인증 방법과 달리 상태를 유지하지 않아 stateless하다고 한다.


#### 2. JWT 구조
    Header.Payload.Signiture
- Header: Token Type(토큰의 종류), Hash Algorithm(token을 hash로 암호화할 때 사용할 algorithm) 정보를 담는다.
- Payload: Body라고도 하며, client의 정보, metadata 정보를 담는다.
- Signiture: (Encoding Header + Encoding Payload)를 secret key를 활용하여 Hash로 암호화한다.
- Signiture를 생성할 때, Header와 Payload는 각각 base64Url으로 encoding된다.
- encoding은 암호화가 아니다. 따라서 누구나 base64Url을 사용하여 encode/decode 할 수 있다. 그래서 server는 private key를 바탕으로 token의 진위여부를 확인한다.


#### 3. JWT 인증의 장단점
|Pros|Cons|
|----|----|
|Client가 token 정보를 가지기 때문에 server 확장(scale-up)이 용이하다.|Token 정보가 탈취될 수 있어 보안에 취약할 수 있다.|
|Server의 memory 부담이 줄어든다.|Server와 client 사이의 주고받는 데이터가 많다.(Payload에 많은 정보를 포함하기 때문)|
|다양한 Domain에 대응이 가능하다.|Token 인증을 위해 매번 DB를 조회하여 DB에 부하가 올 수 있다.|
|Client가 server로 요청할 때 더 이상 Cookie를 전달하지 않아 쿠키를 사용하면서 생기는 보안 취약성이 사라진다.||


#### 4. Refresh Token?
- Access token은 탈취 당할 수 있는 확률이 있기 때문에 보안을 위해 만료 시간을 설정해서 만료될 때마다 새로 발급해야한다. 이러한 보안상 불편함을 해소하기 위해 사용하는 것이 refresh token이다.
- Refresh token은 access token을 발행할 때 함께 발행된다. 내용은 같지만 refresh token은 만료 시간을 길게 생성한다. 그 이유는 access token이 만료되었을 때 다시 로그인하지 않고 refresh token의 유효기간이 남아있으면 그 refresh token을 사용하여 access token을 재발급 받을 수 있도록 하기 위함이다.
- Refresh token의 만료기간이 길어서 걱정할 수 있지만, access token의 정보를 얻기 위해서는 client 계정 정보(id와 screte)가 필요하기 때문에 refresh token만 탈취되었을 경우 보안상 큰 문제가 없다.


#### 5. Access Token의 보안
    Q1. 누군가 Payload에 이상한 정보를 넣어 인코딩한 후 가짜 데이터를 보내면?
Server에서 받은 secret key로 열리는 access token과 함께 보내기 때문에 안전하다.

    Q2. JWT가 탈취당하면?
JWT Token은 탈취 당할 수 있다. 따라서 access token의 만료 기한을 설정한다. 보통 15분이고, 짧을수록 보안에 좋지만 너무 짧으면 매번 새롭게 인증해야 하므로 사용자가 불편함을 느낄 수 있다.

<br>

## 참고자료
- https://sherryhsu.medium.com/session-vs-token-based-authentication-11a6c5ac45e4
- https://yonghyunlee.gitlab.io/node/jwt/
- https://develoger.kr/grphql을-사용하는-frontend에서-jwt다루기/
- https://mangkyu.tistory.com/55
- https://velog.io/@moontae/Access-Token%EA%B3%BC-Refresh-Token
- https://developers.cafe24.com/ko/app/front/develop/oauth/retoken

