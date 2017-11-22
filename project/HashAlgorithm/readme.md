
# Hash Algorithm


<h3>해시 알고리즘 사용사례</h3>

<h4>첫째, 전자서명, 각종 인증서</h4>
공인인증서 발급 시 일련번호, 발급자, 발급대상 등의 정보를 해시 알고리즘을 사용하여 고유한 하나의 해시 값을 얻기 위해 사용합니다

<h4>둘째, 비트코인</h4>
해시 알고리즘의 일 방향 함수 성질을 이용하였습니다. 해시 코드를 만드는 시간은 짧지만 다시 원래 값을 찾는 것은 오래 걸립니다(사실상 불가능). 이 특성을 이용하여 원래 값을 찾는 난이도를 조절하여 찾게 되면(문제를 풀면) 그 사람(컴퓨터)에게 화폐를 지급합니다.

<h4>셋째, 카카오 페이</h4>
거래가 이루어지면 거래정보를 해시 값으로 변경하여 거래내역을 기록하는 장소(블록 체인 같은 공간)에 올리기 위해 사용합니다.

<h4>넷째, 한국은행, 장외주식 거래 인증시스템</h4>
기존 절차는 상대방 확인 후 매도, 매수를 진행했다면, 지금은 휴대폰과 계좌번호 인증을 통해 부여 받은 해시 값으로  인증된 거래를 진행합니다



<br>
<br>

<h3>해시 알고리즘 성질</h3>

<h4>1] 역상 저항성(일 방향 함수)</h4>
원본 데이터를 해시 코드로 만드는 것은 쉽습니다. 그러나 해시 코드로 원본 데이터를 찾기란 불가능합니다

<h4>2] 제 2 역상 저항성</h4>
입력한 데이터의 해시 값과 동일한 해시 값은 갖는 다른 입력 값을 찾을 수 없습니다

<h4>3] 충돌 발생</h4>
기존에 생성된 해시 코드와 동일한 해시 코드 값이 생성 되었을 경우를 의미합니다


<h4>Code</h4>

``` 
public class Main {

public String testMd5(String str) {
    
    String Md5 = "";
    
    try {
    
        MessageDigest md = MessageDigest.getInstance("Md5");

	    md.update(str.getBytes());
	        
	    byte byteData[] = md.digest();

	    StringBuffer sb = new StringBuffer();

        for(int i = 0; i < byteData.length; i++) {

            sb.append(Integer.toString((byteData[i]&0xff) + 0x100,
            16).substring(1));

        }

        Md5 = sb.toString();

    } catch(NoSuchAlgorithmException e) {

        e.printStackTrace();

        Md5 = null;

    }

    return Md5;
}
```

```

public String testSha256(String str) {

    String SHA = "";

    try {

        MessageDigest sh = MessageDigest.getInstance("SHA-256");

        sh.update(str.getBytes());

        byte byteData[] = sh.digest();

        StringBuffer sb = new StringBuffer();

            for(int i=0; i<byteData.length; i++) {	

                   sb.append(Integer.toString((byteData[i]&0xff)+0x100,16).substring(1));
	    
	    }
    
	    SHA = sb.toString();

	    } catch(NoSuchAlgorithmException e) {

	    e.printStackTrace();

	    SHA = null;
    
    }

	return SHA;

}
```

```
	public static void main(String[] args) {

		Main main = new Main();

		System.out.println(main.testMd5("hello"));

		System.out.println("----");

		System.out.println(main.testSha256("hello"));

	}

} 
```

