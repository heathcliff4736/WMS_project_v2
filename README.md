# 🚀 RACL WMS 프로젝트 (Builders 팀)

[![Java](https://img.shields.io/badge/Java-17-blue)](https://www.java.com/)
[![Spring](https://img.shields.io/badge/Spring-Framework-6DB33F)](https://spring.io/)
[![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1)](https://www.mysql.com/)
[![JSP](https://img.shields.io/badge/JSP-Active-orange)](https://www.oracle.com/java/technologies/jspt.html)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-black?logo=github)](https://github.com/)

---

## 📌 프로젝트 개요
- **프로젝트명**: RACL  
- **팀명**: Builders (빌더스)  
- **개발 기간**: 2025.11.07 ~ 2025.11.14  
- **프로젝트 목표**: 스포츠 의류 브랜드 대상 WMS(창고 관리 시스템) 구현  
- **내 담당 기능**: 입고관리(Inbound Management)

---

## 👥 팀원 및 역할
| 역할 | 이름 | GitHub |
|------|------|--------|
| 팀장 / 입고관리 | 엄현석 | [@heathcliff4736](https://github.com/heathcliff4736) |
| Git Master / 대시보드, 재무관리 | 김형근 | [@geeunii](https://github.com/geeunii) |
| 팀원 / 재고관리 | 박용헌 | [@00parkyh](https://github.com/00parkyh) |
| 서기 / 로그인, 회원관리, 고객센터 | 김도윤 | [@doyooning](https://github.com/doyooning) |
| 팀원 / 출고관리 | 장현우 | [@fsdawer](https://github.com/fsdawer) |
| 팀원 / 창고관리 | 이재훈 | [@jaehoon0321](https://github.com/jaehoon0321) |

---

## ⚙️ 기술 스택 (간략)
**Frontend**: HTML5, CSS3, JavaScript, jQuery, Bootstrap  
**Backend**: Java 17, Spring Framework, Spring MVC, MyBatis, JSP, Tomcat  
**Database**: MySQL  
**협업 도구**: Git, GitHub, IntelliJ IDEA

---

## 💡 입고관리 기능 (Inbound Management)
내가 담당한 입고관리 기능은 **입고 요청 생성, 수정, 승인, 반려, 취소**를 포함하며, 아래와 같은 특징이 있습니다:

- **PRG 패턴**: 중복 요청 방지, 새로고침 시 데이터 중복 입력 방지  
- **트랜잭션 관리**: 여러 테이블 변경 시 부분 실패 방지 (`@Transactional`)  
- **AJAX 활용**: 카테고리 선택 → 상품 목록 동적 로드, 상태별 필터링 시 페이지 새로고침 없이 데이터 갱신  
- **MyBatis 활용**: SQL과 Java 코드 분리로 유지보수 용이  

### 📝 간략 예시 코드
```java
@Transactional
public InboundRequestDTO createInbound(InboundRequestDTO dto) {
    int inboundId = insertInbound(dto); // Inbound, Inbound_Item 테이블 동시 처리
    return dto;
}
```

### 🔄 기능 흐름
```mermaid
flowchart TD
    A[입고 요청 생성 폼] --> B[카테고리 선택]
    B --> C[AJAX로 상품 목록 로드]
    C --> D[입고 요청 생성/수정/취소]
    D --> E[서버: @Transactional + MyBatis 처리]
    E --> F[PRG 패턴으로 리다이렉트]
    F --> G[입고 리스트 상태별 필터링 (AJAX)]
```

---

## 🌿 브랜치 전략 (간략)
```
main      # 최종 배포용
develop   # 통합 개발 브랜치
dev/XXX   # 개인 작업 브랜치
```
- 브랜치 네이밍 예: `dev/KHG`, `fix/signup-bug-KHG`, `docs/readme-update-KHG`

---

## 📁 주요 파일 구조
```
src/
 ├─ main/
 │   ├─ java/com/ssg/wms/inbound/service
 │   │   ├─ InboundAdminServiceImpl.java
 │   │   └─ InboundMemberServiceImpl.java
 │   ├─ resources/
 │       └─ mappers/          # MyBatis Mapper XML
 │       └─ templates/
 │           └─ inbound/      # JSP 입고 관련 뷰
```

---

## 🔗 참고
- 팀장 & 입고관리 담당으로 핵심 모듈 구현 및 유지보수  
- 깃허브에서 프로젝트 전체 코드와 함께 입고관리 모듈 확인 가능

---

💡 **Tip**: 코드 예시는 간략화하여 핵심 로직만 표시, 전체 구현은 GitHub에서 확인 가능
