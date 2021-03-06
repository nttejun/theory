## AES : 고급 암호화 표준(Advanced Encryption Standard) ##

<br>
<h3>AES (고급 암호화 표준)</h3>

일반적인 블록 크기 : 64비트, 128비트(3)<br>

최근 메신저들은 AES 128Bit 이상의 암호화 알고리즘 사용(6)

AES 알고리즘 블록 크기 : 128비트, 192비트, 256비트<br>

<br>
<h3>블록 암호 운용 방식이란</h3>

가변 길이 데이터를 암호화(블록암호)하기 위해 먼저 단위 블록 들로 나누고 어떻게 암호화 할 것인지 정하는데, 이때 블록 들의 암호화 방식을 운용 방식이라고 합니다<br>

<br>
<h4>블록 암호 운용 방식은 왜 사용하는가?</h4>

하나의 키를 사용하면서 블록 암호를 반복적으로 안전하게 사용하도록 만드는 방법입니다<br>

> 블록암호란? 중요 정보를 정해진 블록 단위로 암호화(대칭 키 암호 시스템)


<br>
<h3>블록 암호 운영 방식 종류</h3>

- ECB (Electronic Code Book) 전자 부효표 방식
	- 암호화 할 메시지를 **여러 블록으로 나누고 각각 암호화** 하는 방식

- CBC (Cipher Block Chaining) 암호 블록 연쇄 방식
	- 각 블록은 암호화 되기 전 **이진 블록의 암호화 결과와 XOR**되며, 첫 블록에 벡터를 사용(매 암호화 마다 다른 초기화 백터 사용필요)

- OFB (Output FeedBack) 출력 피드백 방식
	- XOR 명령의 대칭 때문에 **암호화와 암호 해제** 방식이 완전히 동일

- CFB (Cipher FeedBack) 암호 피드백 방식
	-** CBC 변형**으로 블록 암호를 **자기 동기 스트림 암호**로 변환
> 자기 동기 스트림 암호란 난수열을 생성할 때 **암호화 키**와 함께 이전에 **암호화된 문자열 일부**를 사용

- CTR (Counter) 카운터 방식
	- 블록 암호를 **스트림 암호**로 바꾸는 구조
	- 각 블록마다 **현재 블록이 몇 번째**인지 얻고 **그 숫자와 nonce를 결합해** 블록 암호의 입력으로 사용
	- 그렇게 각 블록에서 **연속적인 난수를 얻어** 다음 **암호화 하려는 문자열**과 XOR 한다
	- 카운터 방식은 각 블록의 암호화 및 복호화가 이전 블록에 의존하지 않아 **병렬적 동작**이 가능
	- 원하는 암호화된 문자열만 부분 복호화도 가능

> Nonce는 임의로 생성되는 암호화 토큰(8)

<br>
<h3>패딩</h3>
블록 가장 마지막에 공백이나 의미 없는 기호 등을 추가해서 블록을 고정된 길이로 만드는 것

<br>
<h4>암호화 처리에 사용하는 패딩</h4>
비트는 배수 단위로 증가하며 블록을 채울 수 있다. 마지막 블록이 배수로 채울 수 없는 경우에 패딩 방식을 이용한다

> 예를들면 암호화 처리 시 
> 10bit 단위로 처리
> 블록 길이 100bit, 250bit 문제 없다
> 그러나 105bit 는 5bit 남는 문제발생
> 패딩으로 5bit 길이를 채운다


<br>
<h3>AES 알고리즘이 구현되는 과정</h3>

- AES 알고리즘 구현에 사용되는 알고리즘(7)
	- SubBytes
	- ShiftRows
	- MixColumns
	- AddRoundKey

- 각 라운드에서 대체와 치환을 이용해서 데이터 블록 전체를 병렬 처리한다

- 입력 키를 44개의 32비트 워드로 배열로 확장<br>

- 4개의 서로 다른 워드(128비트)를 각 라운드에서 라운드 키로 사용<br>

- 네 가지 단계를 이용, 한 번의 치환과 세 번의 대체
	- 1 바이트 대체 (Substitute bytes)
		- 블록을 바이트 단위 형태로 교환합니다 
	- 2 행 이동 (Shift rows)
		- 단순히 행과 행을 치환
	- 3 열 섞기 (Mix columns)
		- 열(rows)에 속한 모든 바이트를 순환 행렬을 사용해 함수로 열에 있는 각 바이트를 대체하여 변화시킨다
	- 4 라운드 키 더하기 (Add round key)
		- 확장된 키 일부와 현재 블록은 비트별로 XOR

- 오직 라운드 키 더하기 단계에서만 키를 사용합니다<br>

- 블록에 XOR 암호화를 하고, 그 다음 블록을 뒤섞고, 그 뒤에 다시 XOR 암호화를 하는 것을 번갈아 적용하면서 보완성이 강화되는 단계를 거치게 된다<br>

- 각 단계는 역으로 계산하기 쉽다
> 역 계산 : 바이트 대체, 행이동, 열 섞기 단계<br>

- 진행된 단계를 복호화를 통하면 평문을 빠르게 얻을 수 있다는 의미<br>

- 확장 키 순서를 뒤집는 일반적인 블록 암호방식과 AES는 다르다<br>

- 4단계가 모두 역 계산이 가능해 복호화를 평문으로 얻을 수 있다<br>

- 암호화 복호의 마지막 라운드는 오직 세 단계로만 구성되는데 이것이 AES 구조가 가진 특징이고, 이 특성은 AES 암호가 역으로 작동되기 위해 필요(1)<br>



<br>
<h4>참고문헌</h4>
(1) - https://ko.wikipedia.org/wiki/고급_암호화_표준<br>
(2) - https://ko.wikipedia.org/wiki/%EB%B8%94%EB%A1%9D_%EC%95%94%ED%98%B8_%EC%9A%B4%EC%9A%A9_%EB%B0%A9%EC%8B%9D <br>
(3) - https://www.ibm.com/support/knowledgecenter/ko/SSWPVP_2.7.0/com.ibm.sklm.doc/overview/cpt/cpt_ic_oview_tech_cryptographic_algorithm.html <br>
(4) - http://acaasia.blogspot.kr/2013/07/padding-mode.html <br>
(5) - https://ko.wikipedia.org/wiki/%ED%8C%A8%EB%94%A9_(%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4) <br>
(6) - http://platum.kr/archives/30613 <br>
(7) - https://namu.wiki/w/AES <br>
(8) - https://www.ibm.com/support/knowledgecenter/ko/SSEQTP_8.0.0/com.ibm.websphere.base.doc/info/aes/ae/cwbs_noncev6.html <br>