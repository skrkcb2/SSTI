# SSTI
### 특징: 이름 그대로 서버 쪽 템플릿 인젝션(Server Side Template Injection) 이다. 서버의 템플릿 엔진이 특정 구문에 타임리프의 경우(SPEL)을 실행 코드로 해석하여 RCE(원격 코드 실행)을 행할수 있는 취약점 이다.
#### 해당의 경우는 템플릿 엔진에서 발생 하는 인젝션 임으로 취약점이 있는 버전의 템플릿 엔진을 설정 해야 테스트가 가능하다(여러 템플릿 엔진이 존재하나 저는 Thymeleaf의 케이스를 확인했습니다).
#### 취약 환경: Spring Boot Admin <= 3.1.0 RELEASE / Tymeleaf <= 3.1.1 RELEASE
#### 공격 예시 1 / 공격 구문 : ${T(java.lang.Runtime).getRuntime().exec('calc')} (SPEL / Spring Expression Language)
![SSTI](https://github.com/user-attachments/assets/355b0362-2200-4c5f-b166-66d4b28903f3)
### 취약점 원인:  
#### 사용자 입력을 템플릿 엔진이 처리하면서  SpringEL과 같은 표현 언어 를 실행할 수 있게 되어 발생합니다. 예를 들어, 사용자가 입력한 데이터가 템플릿에서 변수로 사용되며, 그 입력이 템플릿 표현식으로 해석될 경우 악의적인 코드를 실행할 수 있습니다.
### 보안 방법:  
#### Thymeleaf의 업데이트 및 코드 수정

