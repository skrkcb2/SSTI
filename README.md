# SSTI
### 특징: 이름 그대로 서버 쪽 템플릿 인젝션(Server Side Template Injection) 이다. 서버의 템플릿 엔진이 특정 구문에 타임리프의 경우(SPEL)을 실행 코드로 해석하여 RCE(원격 코드 실행)을 행할수 있는 취약점 이다.
#### 해당의 경우는 템플릿 엔진에서 발생 하는 인젝션 임으로 취약점이 있는 버전의 템플릿 엔진을 설정 해야 테스트가 가능하다(여러 템플릿 엔진이 존재하나 저는 Thymeleaf의 케이스를 확인했습니다).
#### 취약 환경: Spring Boot Admin <= 3.1.0 RELEASE / Tymeleaf <= 3.1.1 RELEASE
#### 공격 예시 1 / 공격 구문 : ${T(java.lang.Runtime).getRuntime().exec('calc')} (SPEL / Spring Expression Language)
![SSTI](https://github.com/user-attachments/assets/355b0362-2200-4c5f-b166-66d4b28903f3)
