---
title: 실리콘 벨리 첫번째 주 금요일
date: 2022-06-30 10:00:00 +0900
categories: [2022 미국 실리콘밸리 SW교육프로그램]
tags: [silicon_1week, what_silicon]     # TAG names should always be lowercase
---

# silicon_1week_Friday

## 해야 할일 API 각종 검색해오기.

### API 문서 어떻게 할것인지.

- Swagger
    - Open Api Specification를 위한 프레임워크다.
    - Tools for implementing the specification
    - 주석의 포맷 형식을 맞추지 않거나 오타, 흐름에 맞지 않는 명시들을 할 경우 화면에 표현이 되지 않거나 작동하지 않는다.
    - 만약 작성한 내용에 문제가 있음녀 콘솔 로그로 문제가 있는 위치를 지적하고 원인을 설명
    - 적용시킨 APP의 이름과 API 목록을 알 수 있다.
    - 단점
        - 매우 긴 주석 작성 필요
        - swagger 문법을 배워야 한다.
- Postman
    - ~~적용시킨 APP의 이름과 API 목록을 알 수 있다.~~
    - API 테스트를 할 수 있다.
    - Request → Response

### API 개발할 것을 미리 알아오기.

- 웹캠 처리를 위해 openCV 사용
- 랭킹 처리 api 자체 구현 가능할지도.. 정렬처리하면 될듯.
- 초대 알림 API - Chat API
- 사용자 정보 API
- from django.views.decorators import gzip
- from django.http import StreamingHttpResponse - 웹캠 api
- 그룹 채팅방
    - Agora SDK 그룹채팅방 구현법1
        - 인터넷 전화 통화 서비스와 같다.
    - **WebRTC - API 그룹채팅방 구현법 2**
        - 별다른 소프트웨어 없이 카메라, 마이크 등을 사용해서 실시간 커뮤니케이션 제공하는 기술
        - P2P 방식
        - RealTime 가능
        - STUN/TURN 서버가 꼭 필요
- DRF
    - DB data → JSON CRUD
    - Serializer
    - ModelSerializer
    - 한번에 데이터를 이동시킴으로 정보 전달.

### ex) GET POST DELETE UPDATE - DRF

- GET 방식
    - ex) [http://www.naver.com/index/?parameter=value](http://www.naver.com/index/?parameter=value)
    - GET 방식의 대표적인 특징은 URL 뒤에 파라미터를 붙여서 전송 URL 뒤에 ? 붙이고 &를 통해 여러개의 파라미터 구분
    - 데이터 정송 양에 길이 제한 - 한번 요청에 255자 1.1 에서는 2048자 보안적으로 안전 x
    - GET 방식일 때 URL 붙이기.
- POST 방식
    - body { "parameter":"value", ... }
    - 보디 영역에 데이터를 실어서 보냄.
    - 데이터 전송량의 길이 제한이 없고 대용량 데이터를 보내는 데 적합. 비교적 안전.
    - POST 방식일 때 form에 싸서 submit
- database-abstraction API
    - CREATE = SQL 문의 INSERT
        - p = Person.objects.create(first_name = “Bruce”, last_name = “Springsteem”)
    - UPDATE = 바꿈.
        - [b5.name](http://b5.name) = ‘New name’
        - b5.save()
    - DELETE = 지운다 sql문 비슷한듯
        - e.delete()

### 명령어가 어떻게 전달을 하는지, 503 등등 오류 번호 정하기.

- views.py
    - FBV - 함수 기반의 뷰
    - CBV - 클래스 기반의 뷰
    - CRUD하여 데이터 베이스에 반영 그리고 프론트의 요청에 직접적으로 응답하는 직접적인 기능 담당.
    - URL에서 불러지는 함수가 정확히 어떤 행동을 해야 하는지를 모아둔 파일
        - ex)
        
        tistory로 예를 들자면, 내가 [gimkuku0708.tistory.com/20](http://gimkuku0708.tistory.com/20) 이라는 url로 method GET을 보냈으면,
        
        20번째 게시글이 들어와야 한다.
        
        이때, [views.py](http://views.py/) 에서는 def get 일때 pk가 20번째 인 게시글을 찾고, 이를 return 해주는 함수
        
    
- models.py
    
    database와 연결을 의미
    

- serializer 이란
    
    queryset과 모델 인스턴스와 같은 복잡한 데이터를 json, xml 또는 다른 콘텐츠 유형으로 쉽게 변환 가능.
    
- urls 란
    
    내가 작성한 클래스와 URL 주소를 연결
    
    URL주소로 변경시켜준다.
    

## 상태코드

- 1xx (정보)
    - 요청을 받아들었으며 작업을 계속함.
- 2xx (성공)
    - 요청을 성공적으로 받았으며 인식했고 수용함.
- 3xx (리다이렉션)
    - 요청 완료를 위해 추가 작업 조치가 필요.
    - 
- 4xx (클라이언트 오류)
    - 요청의 문법이 잘못되었거나 요청을 처리할 수 없음.
    - 
    
    400(잘못된 요청): 서버가 요청의 구문을 인식하지 못했다.
    
    401(권한 없음): 이 요청은 인증이 필요함
    
    403(Forbidden, 금지됨): 서버가 요청을 거부함
    
    - ex) 사용자가 리소스에 대한 필요권한을 갖고있지않음
    
    404(Not Found, 찾을 수 없음): 서버가 요청한 페이지(Resource)를 찾을 수 없음.
    
    - ex) 서버에 존재하지 않는 페이지에 대한 요청이 있을 경우 서버는 이 코드를 제공
    - 
- 5xx (서버 오류)
    - 서버가 명백히 유효한 요청에 대해 충족을 실패함
    
    500(내부 서버 오류): 서버에 오류가 발생하여 요청을 수행할 수 없다.
    
    501(구현되지 않음): 서버에 요청을 수행할 수 있는 기능이 없다.
    
- 따로 추가해야 할것들.
    - 결과 값 생성 오류 - 결과 값의 이상이 있을때 ex) 시간이 minus 4xx
    - openCV 연결 서버 오류 5xx
    - 친구 정보 불러오기 오류 - 5xx
    - 친구 알림 보내기 오류 - 5xx


