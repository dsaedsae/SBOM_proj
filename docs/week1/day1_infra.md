# [Day 1] SBOM 프로젝트 인프라 구축: Dependency-Track & Ngrok

> **작성일**: 2025.11.25
> **주제**: 오픈소스 관리를 위한 Dependency-Track 서버 구축과 외부 접속 허용
> **태그**: #Security #SBOM #Docker #DependencyTrack #Ngrok

## 1. 오늘의 목표 
- [o] Docker를 활용해 로컬 환경에 Dependency-Track 서버 구축
- [o] 관리자 대시보드 접속 및 초기 설정
- [o] Ngrok을 이용해 외부(GitHub)에서 내 노트북으로 접속할 수 있도록 터널링

---

## 2. 배운점 (Key Takeaways) 

### 2.1 Dependency-Track이란?
단순히 취약점을 한 번 스캔하고 끝나는 도구(Trivy)와 달리, **조직의 모든 소프트웨어 자산을 지속적으로 모니터링하는 플랫폼**이다.
- **CCTV**에 비유할 수 있다. 어제는 안전했던 라이브러리가 오늘 취약해지면 즉시 알람을 준다.
- **Trivy**는 들어오는 문을 지키는 문지기(CI/CD)고, **Dependency-Track**은 내부 자산을 관리하는 관제탑이다.

### 2.2 왜 Docker를 사용했는가?
Dependency-Track은 Java 기반의 복잡한 웹 애플리케이션이다. 이를 내 노트북에 직접 설치하려면 JDK 버전 맞추기, 환경 변수 설정 등 복잡한 과정이 필요하다.
Docker 이미지를 사용하면 **"제작자가 세팅해둔 환경 그대로"** 컨테이너만 띄우면 되므로 구축 시간을 획기적으로 단축할 수 있었다.

---

## 3. 트러블 슈팅 (Trouble Shooting) 

###  문제 발생: Ngrok 인증 에러
Ngrok 실행 시 다음과 같은 에러가 발생하며 실행되지 않음.
```bash
ERROR:  authentication failed: Usage of ngrok requires a verified account and authtoken.
ERROR:  ERR_NGROK_4018
```

---

## 4. 초기 화면

![diagram](day1_infra.png)