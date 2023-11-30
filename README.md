# DRF_GPT_Project
- Django Rest Framework를 이용하여 챗봇 애플리케이션 구현

## 1. 목표와 기능

### 1.1 목표
- DRF를 이용하여 서버 구현
- 기존 OpenAI에서 제공하는 API를 직접 만든 서버를 통해 요청하도록 변경
- 예산 계획을 세워주는 챗봇 애플리케이션 구현

### 1.2 기능
1) 주요기능
   - 월 수입, 고정지출를 입력하고 장기적인 목표를 설정하면 투자방식을 알려주고
     한달, 한주간 생활비를 계획.
2) 요구사항
   - 회원가입, 로그인 기능 구현
   - ChatGPT로 요청을 보내주는 API를 Django내 구현
     (프론트 엔드->Django 서버->OpenAI api->Django서버에서 응답하고 프론트엔드로 전달->반영)
   - 챗봇 api는 로그인한 유저만 사용가능
   - 각 user 당 하루 5번 사용가능
   - 채팅 DB에 저장
   - 저장된 채팅 내역 조회는 로그인한 본인만 확인가능

## 개발환경

### 2.1 개발환경
FE : Bootstrap
BE : PYTHON, Django


## 3. 프로젝트 구조와 개발 일정

### 3.1 프로젝트 구조
-DB모델
-URL 구조
![image](https://github.com/hoyonzz/project_Blog/assets/129498722/38cfc6b4-1a32-45e8-b9f2-1483590e64a4)


## 4. 메인 기능
- 로그인, 회원가입 기능 DRF구현
- GPT연동
- 월 수입, 고정지출(통신비, 주거비, 부채 등 기타 지출), 목표(저축 및 투자) 금액 입력 후 목표 금액을 프롬프트로 차례대로 입력하면 한달, 한주동안 사용가능한 예산을 알려주는 챗봇 구현
## 7. 추가 기능
- 채팅 서비스를 이용하기 쉽게 프롬프트 제작
1) 월 수입 : (--만원)
2) 통신비(인터넷, 핸드폰, 구독료): (--만원)
3) 부채 등 기타 지출: (--만원)
4) 목표 금액(투자 및 저축): (--만원)
5) 예산 계획 기간: (월간 or 주간)

## 8. 개발 이슈
1) Dango에서 기본으로 제공하는 User모델과 정의한 User모델 충돌하여 오류 발생.
-> AUTH_USER_MODEL = 'accounts.User' 설정값을 추가하여 충돌 문제 해결
2) Chat/models.py에 모델 작성 후 python manage.py makemigrations 명령 수행 시 오류 발생.
(InconsistentMigrationsHistory오류)
-> 데이터베이스 마이그레이션이 일부 진행된 경우에 발생한다고 판단 후 db.sqlite3파일 삭제 후 python manage.py makemigrations와 python manage.py migrate를 다시 실행

