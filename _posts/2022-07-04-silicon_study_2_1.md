---
title: 실리콘 벨리 두번째 주 월요일
date: 2022-06-30 10:00:00 +0900
categories: [2022 미국 실리콘밸리 SW교육프로그램]
tags: [silicon_1week, what_silicon]     # TAG names should always be lowercase
---

# silicon_2week_Monday

## static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT) 이란?

- static 폴더는 css파일, 이미지 파일처럼 사이트에 필요한 정적인 파일들을 모아놓은 것이다. 개발자가 이미지나 파일을 추가하지 않는 이상 현 상태가 계속 유지된다.

```
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('core.urls')),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

## [apps.py](http://apps.py) 란

- 앱에 대한 기본 설정 정보를 담고 있는 파일.

## `models.DateTimeField` 이란?

- 현재 시간 자동 저장.

ex1) `created_at **=** models**.**DateTimeField(auto_now_add**=**True)` 

- 해당 레코드 생성시 현재 시간 자동 저장.

ex2) `updated_at **=** models**.**DateTimeField(auto_now**=**True)` 

- 해당 레코드 갱신시 현재 시간 자동 저장.

## `get_context_data` 이란?

- 추가 context 추가

```
		def get_context_data(self, **kwargs):				
				# 기본 구현을 호출해 context를 가져온다.
        context = super(PublisherDetail, self).get_context_data(**kwargs)
        # 모든 책을 쿼리한 집합을 context 객체에 추가한다.
        context['book_list'] = Book.objects.all()
        return context
```

## `form_valid` 이란?

- 유효한 폼 데이터로 처리할 로직 코딩. 반드시 super() 함수를 호출해야 함.
- 클래스형 뷰 폼처리 = FormView를 상속받은 폼처리

```python
class MyView(View):
    template_name = 'mytemplate.html'
		if form.is_valid():
	    		#cleaned_data로 관련 로직 처리
	        return HttpResponseRedirect('/success/')
	  return render(request, self.template_name, {'form':form})
```

```python
class MyView(FormView):
    success_url = '/success/' # MyFormView 처리가 정상적으로 완료되었을 때 리다이렉트 될 URL
    form_class = MyForm      # 사용자에 보여줄 폼을 정의한 forms.py 파일 내의 클래스 명.
    template_name = 'mytemplate.html' # 폼을 포함하여 렌더링할 템플릿 파일 이름
    def form_valid(self, form)
        return super(MymView, self).form_valid(form)
```

## view.py

```
#url 매치.
def index(request):
	return HttpResponse("index page")
```

## urls.py

```
# url 연동.
urlpatterns = [
    path('',views.index, name='index') # 첫번째가 endpoint
]
```

## setting.py

- 추가한 것들 api 셋팅 필요!

## `@admin.register(Ranking)` 이란?

= `admin.site.register(Ranking, RankingAdmin)`

- 기본 ModelAdmin으로 등록한다.

## cv2 설치

- pip install opencv-python
- `pip install opencv-contrib-python`

## Pycharm - `requirement.txt` 가 있을때!

- **pip install -r requirement.txt**
    - 요구 모듈들을 한번에 다운할 수 있다..
    

## Pycharm - [model.py](http://model.py) - makemigrations

- makemigration
- migrate

---

## pip install tensorflow - error 해결법.1

[Windows 11/10에서 Win32 긴 경로를 활성화 또는 비활성화하는 방법 - Windows789](https://windows789.com/ko/windows-11-10%EC%97%90%EC%84%9C-win32-%EA%B8%B4-%EA%B2%BD%EB%A1%9C%EB%A5%BC-%ED%99%9C%EC%84%B1%ED%99%94-%EB%98%90%EB%8A%94-%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)

---

# AI 학습도 똑같은 사례

[AI학습도 PROTOTYPE (1/2)](https://www.youtube.com/watch?v=Kb44BITlJ18)

# Django 랭킹 개발 사례

[첫번째 Django 연습용 프로젝트 07: 랭킹 모델 생성 & 뷰, 템플릿 연동](https://semtax.tistory.com/57?category=804337)

[Chirpy 테마 커스터마이징](https://www.irgroup.org/posts/Chirpy-%ED%85%8C%EB%A7%88-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95/)

## Pycharm 가상환경이 안될때

[윈도우의 powershell에서 가상환경이 활성화 안되는 이유](https://dreamlog.tistory.com/603)

# 웹캠 ai 구동 예시 찾음.

[Mask Detected in Django using OpenCV and Tensorflow](https://www.youtube.com/watch?v=KcsnCGYt928)

- [camera.py](http://camera.py) 가 전체 통괄 주석 필요.