# Authentication

cookie와 session







# Accounts

`django` 에서 기본적으로 `accounts` 주소를 통해 비밀번호 변경과 같은 작업을 제공하고 있으므로 계정관리 `app` 생성 시 이름을 맞춰서 사용하면 `django`에서 계정 관련 구현되어 있는 것들에 대해 편하게 사용가능하다.



- `form`

  ```python
  from django.contrib.auth.forms import (
  	AuthenticationForm,
  	UserCreationForm,
  	PasswordChangeForm,
  	UserChangeForm)
  ```

  1. 계정 생성(sign up) : `UserCreationForm`

     ```python
     def signup(request):
         if request.method == 'POST':
             form = UserCreationForm(request.POST)
             if form.is_valid():
                 user = form.save()
                 # 로그인
                 auth_login(request, user)
                 return redirect('articles:index')
         else:
            form = UserCreationForm()
         context = {
             'form': form,
         }
         return render(request, 'accounts/signup.html', context)
     
     ```

  2. 계정 삭제(delete)

     ```python
     def delete(request):
         if request.user.is_authenticated:
             # 로그인한 상태에서만 계정 삭제 가능
             request.user.delete()
             # 계정삭제후 세션도 삭제해준다.
             auth_logout(request)
     
         return redirect('articles:index')
     
     ```

  3. 계정 정보 변경(update) : `UserChangeForm`

     ```python
     def update(request):
         
         if request.method == 'POST':
             form = UserChangeForm(request.POST, instance=request.user)
             if form.is_valid():
                 form.save()
                 return redirect('articles:index')
         else:
             form = UserChangeForm(instance=request.user)
         context = {
             'form': form,
         }
         return render(request, 'accounts/update.html', context)
     
     ```

     - `UserChangeForm` 사용 시 `admin`권한의 정보들이 노출되기 때문에 `forms.py`에서 custom을 통해 사용한다.

       ```python
       # forms.py
       from django.contrib.auth.forms import UserChangeForm
       from django.contrib.auth import get_user_model
       # from django.contrib.auth.models import User
       
       
       class CustomUserChangeForm(UserChangeForm):
           
           class Meta:
               model = get_user_model()	# 현재 프로젝트에서 활성화된 유저모델 참조
       #        model = User	# 이것도 가능하지만 위를 권장
               fields = ('first_name', 'last_name', 'email',)
           
       ```

  4. 로그인(login) : `AuthenticationForm`

     로그인 시 `django` 내 로그인 기능 구현 함수를 사용하며 우리가 구현할 함수와 이름이 중복되므로 import 시 as를 통해 닉네임을 설정해준다.

     ```python
     from django.contrib.auth import login as auth_login
     
     
     def login(request):
         # 로그인된 상태인데 url주소로 login 접근하는 것 막기
         if request.user.is_authenticated:
             return redirect('articles:index')
         
         if request.method == 'POST':
             form = AuthenticationForm(request, request.POST)
             if form.is_valid():
                 user = form.get_user()
                 auth_login(requets, user)
                 return redirect(request.GET.get('next') or 'articles:index')
     
         else:
             # 로그인 화면
             form = AuthenticationForm()
         context = {
             'form': form,
         }
         return render(request, 'accounts/login.html', context)
     ```

  5. 로그아웃(logout)

     ```python
     from django.views.decorators.http import require_POST
     from django.contrib.auth import logout as auth_logout
     
     
     # POST 요청만 받는다
     @require_POST
     def logout(requets):
         # 로그인 된 상태에서만 세션 삭제
         if requset.user.is_authenticated:
             auth_logout(requets)
         return redirect('articles:index')
             
     ```

  6. 비밀번호 변경(change_password) : `PasswordChangeForm`

     ```python
     from django.contrib.auth import update_session_auth_hash
     
     
     def change_password(request):
         if request.method == 'POST':
             form = PasswordChangeForm(request.user, request.POST)
             if form.is_valid():
                 user = form.save()
                 # 세션 변경
                 update_session_auth_hash(request, user)
                 return redirect('articles:index')            
         else:
             form = PasswordChangeForm(request.user)
         context = {
             'form': form,
         }
         retunr render(request, 'accounts/chanage_password.html', context)
     ```

     

-----

user 정보

request.user

user = form.save()

form.user

user = form.get_user()