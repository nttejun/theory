## public-key cryptography (비대칭키  알고리즘) ##

<h3>비대칭 알고리즘</h3>

공개 키 암호를 구현하는 알고리즘(1)

<br>
<h3>공개 키 암호 방식</h3>

사전에 비밀 키를 나눠가지지 않은 사용자들이 안전하게 통신할 수 있도록 합니다

> Ex - 편지함 : 입구가 어딘지 알면(공개키) 구멍은 좁지만 누구나 편지를 넣을 수 있다. 편지함 개봉은 자물쇠 키를 보유한 소유자만 편지함을 열어 내용을 확인 할 수 있다

공개 키와 비밀 키가 존재하며, 공개 키는 누구나 알 수 있지만 그에 대응하는 비밀 키는 소유자만 알 수 있습니다<br>

공개키로 제출은 가능하나 제출된 내용들은 비밀키를 가진 소유자만 접근할 수 있습니다

<br>
<h4>공개 키 암호 방식 2가지</h4>

- 공개 키는 누구나 알 수 있는 권한보유

- 암호 키는 키 소유자만 알 수 있는 권한보유

<br>
<h4>공개 키 알고리즘 종류(2)</h4>

- RSA (Rivest, Shamir and Adleman)
	- 암호화를 인증할 시 사용

- ElGamal
	- 시스템은 이전에 대칭 메시지 암호화에 사용 된 키를 비대칭 적으로 암호화하여 추가 보안 계층을 제공합니다. 
	- 난수를 이용한 암호화로 정보보호에 장점안 최초 비대칭 키 알고리즘

- ECC (Elliptic Curve Cryptosystem, 타원 곡선 암호 시스템)
	- 전원 양이 한정된 이동 통신 기기 암호화에 적용 가능하며, 속도가 빠른 구현이 가능

- DH (Diffie-Hellman key exchange)
	- 함호화 되지 않은 통신망을 통해 공통의 비밀 키를 공유할 수 있도록 한다

- DSA (Digital Signature Algorithm)
	- 디지털 서명 표준에 사용하기 위해 제안
	- ElGamal 서명체계의 변형

<br>
<h4>적용사례</h4>

- SSL (Secure Sockets Layer) / TLS (Transport Layer Security)
	- 외부에서 전달하는 정보를 중간에 훼손, 변경되지 않고 안전하게 전달받는 것이 목적
	- TCP/HTTP를 이용한 데이터 통신

<br>
<h4>참고자료</h4>
(1) - https://ko.wikipedia.org/wiki/%EA%B3%B5%EA%B0%9C_%ED%82%A4_%EC%95%94%ED%98%B8_%EB%B0%A9%EC%8B%9D <br>
(2) - https://seed.kisa.or.kr/iwt/ko/intro/EgovPublicKey.do <br>