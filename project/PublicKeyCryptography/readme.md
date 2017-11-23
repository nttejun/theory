## public-key cryptography (비대칭키  알고리즘) ##

<h3>비대칭 알고리즘</h3>

공개 키 암호를 구현하는 알고리즘(1)

<br>
<h3>공개 키 암호 방식</h3>

사전에 비밀 키를 나눠 기지지 않은 사용자들이 안전하게 통신할 수 있도록 합니다

> Ex - 편지함 : 입구가 어딘지 알면(공개키) 구멍은 좁지만 누구나 편지를 넣을 수 있다. 편지함 개봉은 자물쇠 키를 보유한 소유자만 편지함을 열어 내용을 확인 할 수 있다

<br>
<h4>공개 키 암호 방식 2가지</h4>

- 공개 키는 누구나 알 수 있는 권한보유

- 암호 키는 키 소유자만 알 수 있는 권한보유

<br>
<h4>공개 키 알고리즘 종류(2)</h4>

- RSA (Rivest, Shamir and Adleman)
	- 암호화를 인증할 시 사용

- ElGamal
	- 난수를 이용한 암호화로 정보보호에 장점안 최초 비대칭 키 알고리즘

- ECC (Elliptic Curve Cryptosystem, 타원 곡선 암호 시스템)
	- 전원 양이 한정된 이동 통신 기기 암호화에 적용 가능하며, 속도가 빠른 구현이 가능

- 전자 서명 (Digital signature)
	- 인증을 위한 디지털 인감 역할
	> 처리할 문서를 자신의 개인 키로 암호화해 전달한다. 수신자는 공개 키로 복호화 하면 누구 서명의 문서내용인지 알 수 있다

<br>
<h4>참고자료</h4>
(1) - https://ko.wikipedia.org/wiki/%EA%B3%B5%EA%B0%9C_%ED%82%A4_%EC%95%94%ED%98%B8_%EB%B0%A9%EC%8B%9D <br>
(2) - https://seed.kisa.or.kr/iwt/ko/intro/EgovPublicKey.do <br>