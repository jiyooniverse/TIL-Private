# Model/Form

## 1. Model 

각 `app`에서 사용할 data들에 대해 data 구조를 `models.py`에 작성한다.

```python
from django.db import models


class MyModel(models.Model):
    title = models.CharField(max_length=100)
    ...
    
```



`Model`에서 정의한 구조의 `database`를 생성한다. 아래 명령어 실행 시 `<app_name>_MyModel`의 table이 생성된다.

```bash
python manage.py makemigrations
python manage.py migarte
```



## 2. Form

`Model`에서 정의한 구조 기반으로 `Form`을 생성한다. `Form` 형식을 이용하면 `회원가입` 과  `글작성`  같은 **페이지의 구성**과 입력값에 대한 **유효성 검사**를 간단하게 할 수 있다.

```python
from django import forms
from .models import MyModel


class MyForm(forms.ModelForm):
    
    class Meta:
        model = MyModel		# 참조할 'model명'을 적는다.
        fields = '__all__'	# model에서 정의한 field 중 사용할 field를 선택한다.
        # fields = ('title', 'content')
        # exclude = ('field_a')	# field가 많을 경우 제외할 field 작성 
```



- `views.py` : `form.is_valid()`를 통해 입력값 유효성 검사 가능

  ```python
  def create(request):
      form = MyForm(request.POST)	# MyForm에 데이터 입력
      if form.is_valid():	# 유효성 검사
          form.save()		# 유효한 데이터면 db에 저장하기
          ...
          
  ```

- `---.html` :   `{{ form.as_p }}`으로 작성(입력) 폼 형식 구현 가능

  ```django
    <form action="{% url 'articles:create' %}" method="POST">
      {% csrf_token %}
      {{ form.as_p }}    
      <input type="submit">
    </form>
  ```



----------

##### ** Form 꾸미기

```python
class QuestionForm(forms.ModelForm):
    title = forms.CharField(
        min_length=2,
        max_length=100,
        required=True
    )
    content = forms.CharField(
        widget=forms.Textarea,
        required=True,
        min_length=2,
        max_length=100
    )

    is_save = forms.BooleanField(required=False, label='저장?')

    class Meta:
        model = Question
        fields = '__all__'

        # 아래 필드는, 모델에 있는 것 중에 
        # 데이터 검증 + HTML 생성
        # fields = ('title', 'content', 'category')
        # field가 많을 경우 '__all__'하고 제외할 field 작성
        # exclude = ('field_a', 'field_b')
```

