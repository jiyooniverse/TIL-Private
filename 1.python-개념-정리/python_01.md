#### 00_python_intro

- '1줄 1문장'이 원칙

  ```python
  # 두줄을 한줄로 표기할 때
  # 1.
  print('hello'); print('world')
  # 2.
  print('hello\
        world')
  ```

- 할당 연산자 (=)

  - 데이터 타입 확인 `type()`
  - 메모리 주소 확인 `id()`

  ```python
  # 변수 할당하는 방법
  # 1. 
  x = y = 200
  # 2. 
  x, y = 1, 2
  ```

- 식별자

  ```python
  # keyword 확인
  import keyword
  print(keyword.kwlist)
  ```

  > ['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']

- 숫자

  > 1. python3에서는 `long`타입은 없고 모두 `int`타입으로 표기됨
  >
  > 2. 8진수: 0o/ 2진수: 0b/ 16진수:0x
  >
  > 3. 파이썬에서는 **임의 정밀도 산술**을 사용하기 때문에 **오버플로우**가 없다. 
  >
  > 4. 실수는 `float`형으로 부동소수점을 사용하여 표현하기 때문에, 항상 같은 값으로 일치되지 않는다.(floating point rounding error)
  >
  >    ```python
  >    # 실수 연산
  >    print(3.5 - 3.12 == 0.38)	# False
  >    
  >    # floating point rounding error 처리 방법
  >    # 1. 아주 작은 수(1e-10) 이용
  >    a = 3.5 - 3.12; b = 0.38
  >    abs(a - b) <= 1e-10
  >    
  >    # 2. sys 모듈 이용
  >    import sys
  >    abs(a - b) <= sys.float_info.epsillon
  >    
  >    # 3. math 모듈 이용
  >    import math
  >    math.isclose(a, b)
  >    ```
  >
  > 5.  복소수 표현 
  >
  >    ```python
  >    a = 3 - 4j
  >    a.real	# 3
  >    a.img	# 4
  >    ```

- 문자열 

  ```python
  # ''("") 출력
  # 1. ''("")를 출력하고 싶을 땐 ""('')로 밖을 감싼다.
  print("철수가 말했다. '안녕?'")
  
  # 2. \ 사용
  print("철수가 말했다. \'안녕?\'")
  ```

- 이스케이프 시퀀스

  `\n` : 줄 바꿈, `\t`: 탭, `\r`: 캐리지 리턴, `\0` : 널(Null), `\\`: \, `\'` : ', `\"`:"

- String interpolation: %-formatting, str.format(), f-string

  ```python
  # %-formatting
  print("%s는 %f점을 맞았습니다."%(name,float(score)))
  # str.format()
  print("{}는 {:f}점을 맞았습니다.".format(name,float(score)))
  # f-string
  print(f"{name}은 {flaot(score)}점을 맞았습니다.")
  
  # f-string 형식 지정
  import datetime
  today = datetime.datetime.now()
  print(f"오늘은 {today:%y}년 {today:%m}월 {today:%d}일 {today:%A}") # 오늘은 21년 08월 06일 Friday
  ```

- Boolean

  `False` : 0, 0.0, (), [], {}, '', None

  > 파이썬에서는 값이 없음을 표현하기 위해 `None`타입이 존재함

- 형변환 : 명시적 형변환

  > string -> integer : 형식에 맞는 숫자만 가능 (`int()` ,`float()`)
  >
  > integer -> string : 모두 가능 (`str()`)

- 연산자 

  - 나눗셈`/`은 항상 float를 돌려줍니다. 정수 나눗셈으로 (소수부 없이) 정수 결과를 얻으려면 몫`//` 연산자를 사용합니다.
  -  `==`(`!=`) : 같음(같지않음) / `is` (`is not`): 객체 아이덴티티(부정된 객체 아이덴티티)
    - 파이썬에서 -5부터 256까지의 id는 동일 합니다. 

- 단축평가 : 첫 번째 값이 확실할 때, 두 번째 값은 확인 하지 않습니다.

  ```python
  ('a' and 'b') in 'aeiou' # False
  ('b' and 'a') in 'aeiou' # True
  ```

  

#### 01_data_container

- 시퀀스형 컨테이너 : `list`, `tuple`, `range`, `string`, `binary` 

  > 정렬되어있다(sorted)라는 뜻은 아님!!

  ```python
  # empty tuple
  empty = ()
  # single tutple
  single_tuple = 1,
  
  # range(n, m, s) -> n부터 m-1까지 +s만큼 증가
  list(range(0,-10,-1))	# [0, -1, -2, -3, -4, -5, -6, -6, -8, -9]
  ```

  - 시퀀스형 컨테이너에서 사용가능한 연산자/함수 

    : `in`, `not in`, `+` (concatenation), s`*`n(n번만큼 더하기), `s[i:j]` , `len(s)`, `min(s)`, `max(s)`, `s.count(x)` 

- 비 시퀀스형 컨테이너:  `set`, `dictionary` 

  > `set`는 순서가 없고 중복된 값이 없는 자료구조로 집합과 동일하게 처리됨
  >
  > ```python
  > # set를 이용하면 list 중복값 제거 가능
  > list_a = [1, 2, 3, 1, 1]
  > set(list_a)		# {1, 2, 3}
  > ```

  > `dictionary` 는 `key`와 `value`가 쌍으로 이뤄져있음.
  >
  > `key`는 변경불가능 데이터만 가능 : string, integer, float, boolean, tuple, range

- 변경 가능한 데이터 : `list` , `dict`, `set`

  > 변경 가능한 데이터를 복사할 때는 원본이 바뀌지 않도록 유의하여야 한다.



#### 02_control_flow

- 조건 표현식 (삼항 연산자)

  > true_value if <조건식> else false_value
  >
  > ```python
  > # 절대 값 
  > num = -10
  > value = num if num >= 0 else -num
  > ```

- 반복문

  > while, for

- `enumerate()` : index, value 값 함께 활용 가능

  ```python
  # enumerate() 에 의해 반환되는 인덱스와 값(value)를 함께 출력
  for idx, menu in enumerate(lunch):
      print(idx, menu)
  ```

- `break`, `continue`, `for-else`, `pass` 

  > - for-else : break 문으로 중간에 종료되지 않은 경우만 실행
  >
  > ```python
  > # break가 실행 안됨.
  > for i in range(3):
  >     if i == 100:
  >         print("break가 실행됨.")
  >         break;
  > else:
  >     print("break가 실행 안됨.")
  >     
  > # break가 실행됨.
  > for i in range(3):
  >     if i == 1:
  >         print("break가 실행됨.")
  >         break;
  > else:
  >     print("break가 실행 안됨.")
  > ```

  

#### 03_function

- 함수의 인자

  - 위치 인자 : 기본적으로 인자는 위치에 따라 함수 내에 전달됨.

  - 기본 인자 : 기본값 지정하여 인자 값이 설정되지 않았을 때 사용.

    > **기본 인자 다음에 기본 값이 없는 인자를 사용할 수 없다.**

  - 키워드 인자 : 함수 호출 시 직접 변수의 이름으로 특정 인자를 전달 할 수 있음.

    ```python
    # def greeting(age, name):
    greeting(name='철수', age=24)
    greeting(24, name='철수')
    # greeting(age=24, '철수') # SyntaxError 발생
    ```

    > **키워드 인자 다음에 위치 인자를 활용할 수 없다.**

  - 가변인 인자 리스트 : 개수가 정해지지 않은 임의의 인자를 받기 위해서는 **함수를 정의 할때** `*args`를 활용한다. 가변 인자 리스트는 `tuple`형태로 처리가 되며, 매개변수에 `*`로 표현한다.

    >  활용법
    >
    > ```python 
    > def func(a, b, *args):
    > ```
    >
    > 보통, 이 가변 인자 리스트가 매개변수 목록 마지막에 위치한다.	

  - 가변 키워드 인자 : 가변 키워드 인자는 `dict`형태로 처리가 되며, 매개변수에 `**`로 표현한다.

    > 활용법
    >
    > ```python
    > def func(**kwargs):
    > ```
    >
    > - 식별자는 숫자만으로 구성할 수 없다.
    >
    > - Key가 숫자인 딕셔너리 만드는 방법
    >
    >   ```python
    >   dict([(1, 1), (2, 2)])
    >   dict(((1, 1), (2, 2)))
    >   ```

- 함수 Scope (이름 검색 규칙) : Local < Enclosed < Global < Bulit-in

  ```python
  a = 10
  b = 20
  def enclosed():
      a = 30
      def local():
          c = 40
          print(a, b, c)
      local()
      a = 50
  enclosed()
  ```

  > 30 20 40 

- 상위 스코프 변수를 수정하고 싶다면 global, nonlocal 키워드 활용으로 가능하지만 권장하지 않음.



#### 04_error_exception

- 예외

  - ModuleNotFoundError : 모듈을 찾을 수 없는 경우

    ```python
    import reque
    ```

  - ImportError : 모듈을 찾았느나 가져오는 과정에서 실패하는 경우(존재하지 않는 클래스/ 함수 호출)

    ```python
    import random
    
    random.sampl()
    ```

- 예외 처리

  - `try` & `except`

    - `else` : try절이 예외를 일으키지 않을 때 실행되어야만 하는 코드에 적절.

    - `finally` : 예외 발생 여부와 관계없이 반드시 수행해야할 문장 활용에 사용.

    - `as` : 에러메시지를 나타낼 때 활용

      ```python
      try:
          ...
      except IndexError as err:
          print(f'{err} 발생')
      ```

  - 예외 발생 시키기

    - `raise` : 강제로 에러 발생

      ```python
      raise IndexError('인덱스에러')
      ```

    - `assert` : 상태 검증에 사용되는 에러 발생 시키는 방법

      ```python
      assert len([1, 2]) == 1, '길이 1 아님'
      ```

      

