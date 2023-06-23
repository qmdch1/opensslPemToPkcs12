# opensslPemToPkcs12

SSL 발급을 위해서 도메인이 반드시 필요하다.
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
