# opensslPemToPkcs12

- SSL 발급을 위해서 도메인이 반드시 필요하다.

- 첨부한 Certbot, OpenSSL 알집 파일을 풀어서, Windows - Program Files에 붙여넣기 한다.

- 아래 소스를 실행하면 Cerbot의 경우 C:\Cerbot 이라는 폴더가 생기는데 C:\Certbot\live 에 해당 도메인 폴더가 생기며 폴더안에 키가 발급되어 있다.

- OpenSSL의 경우 명령어 입력시, 암호키를 상단에 표시한 live 도메인폴더 내의 파일을 이용해서 발급하면 된다.
<br><br>

# Let's Encrypt(certbot)<br>
실행경로 : certbot.exe가 실행이 되지 않는다면 run.bat으로 실행하며, cli에서 사용시 certbot은 생략한다.
- Certbot/bin/certbot.exe
- Certbot/run.bat
  
<br><br>
### 인증서 발급
  ```
  certbot certonly --standalone -d [도메인명1] -d [도메인명2]
  ex) certbot certonly --standalone -d www.qmdch.kr
  ```

### 인증서 갱신 (테스트)
  ```
  certbot renew --dry-run
  ```

### 인증서 갱신
  ```
  certbot renew
  ```

### 인증서 확인하기
  ```
  certbot certificates
  ```

<br><br>
# OpenSSL
실행경로
  OpenSSL/bin/openssl.exe 

### 발급받은 pem파일을 pkcs12로 변환하는 command코드
  ```
  openssl pkcs12 -export -inkey [privkey] -in [certificate] -out [배출할키]
  ex) openssl pkcs12 -export -inkey privkey.pem -in fullchain.pem -out keystore.p12
  ```
