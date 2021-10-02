# Python PEP8 Style Guide

\** [공부한 사이트](https://realpython.com/python-pep8/)



## 3. Indentation

파이썬에선 들여쓰기의 단계로 그룹을 결정하므로 들여쓰기는 중요하다.

PEP8에서의 들여쓰기 룰은 다음과 같다.

- 들여쓰기를 나타내기 위해서 4개의 연속적인 space를 사용한다.

- tab보다 space를 선호한다.

  

#### 1\. Tabs vs. Spaces

위에서 언급한 것처럼 들여쓰기를 할때 tab대신에 space를 사용하여야한다. text 편집기에서 tab을 4개의 space로 대신하도록 설정하여 사용할 수 있다. 

파이썬3에서는 tab과 space의 혼용시 자동으로 에러가 발생한다.



#### 2\. Indentation Following Line Breaks

라인 연속성을 사용하여 79글자 이하로 줄을 유지할 때 들여쓰기를 사용하면 가독성 향상에 좋다.

- 여는 구분자에 맞춰 들여쓰기 블록을 맞춘다.

  ```python
  def function(arg_one, arg_two,
               arg_three, arg_four):
      return arg_one
  ```

- `if`문과 같이 4개의 space만 필요한 경우 코드 블럭의 시작을 알기 어려울 수 있다. 이때, 두가지 경우로 가독성을 향상시킬 수 있다.

  - 마지막 조건 다음에 코멘트를 작성하여 구분 할 수 있다. (대부분의 편집기는 코멘트에 문법 하이라이팅 기능이 있어 조건문과 내부 코드를 분리할 수 있다.)

    ```python
    x = 5
    if (x > and
        x < 10):
        # Both conditions satisfied
        print(x)
    ```

  - 연속적으로 작성한 라인에 추가 들여쓰기를 한다.

    ```python
    x = 5
    if (x > 3 and
       		x < 10):
        print(x)
    ```



line break 시 다른 들여쓰기 방법은 **hanging indent**이다. 

첫 번째 줄을 제외한 모든 줄을 들여쓰는 방법으로, 첫 번째 줄에는 어떠한 인자도 있으면 안 된다.

```python
var = function(
	arg_one, arg_two,
	art_three, arg_four)

# 내부 코드와 구분이 필요할 경우 들여쓰기를 추가 할 수 있다.
def function(
		arg_one, arg_two,
		arg_three, arg_four):
    return arg_one

```



#### 3\. Where to Put the Closing Brace

-  닫는 괄호를 그 전 라인의 공백이 아닌 첫 번째 문자에 맞춰 위치시키기

  ```python
  list_of_numbers = [
      1, 2, 3,
      4, 5, 6,
      7, 8, 9
  	]
  ```

-  닫는 괄호를 구조가 시작하는 첫 번째 문자에 맞춰 위치시키기

  ```python
  list_of_numbers = [
      1, 2, 3,
      4, 5, 6,
      7, 8, 9
  ]
  ```

  



## 4. Comments

코드에 코멘트 작성 시 기억할 중요 포인트!

- 코멘트의 길이는 72자 미만으로 제한한다.
- 대문자로 시작하는 완벽한 문장을 사용한다.
- 코드 수정 시 코멘트를 업데이트한다.



#### 1\. Block Comments

- 코드 레벨과 같은 들여쓰기 레벨로 작성한다.

- 각 줄은 `#`과 하나의 공백문자로 시작한다. 

  ```python
  for i in range(0, 10):
      # Loop over i ten times and print out the value of i, followed by a
      # new line character
      print(i, '\n')
  ```

  

-  `#` 를 하나 포함하는 줄로 문단을 나눈다.

  ```python
  def quadratic(a, b, c, x):
      # Calculate the solution to a quadratic equation using the quadratic
      # formula.
      #
      # There are always two solutions to a quadratic equation, x_1 and x_2.
      x_1 = (- b+(b**2-4*a*c)**(1/2)) / (2*a)
      x_2 = (- b-(b**2-4*a*c)**(1/2)) / (2*a)
      return x_1, x_2
  ```



#### 2\. Inline Comments

- 인라인 코멘트를 삼가하여 사용한다.

- 참조하는 문장과 같은 줄에 작성한다.

- 문장으로부터 두개 이상의 공백을 가지고 작성한다.

- 블록 코멘트와 같이 `#`과 하나의 공백문자로 시작한다.

- 명백한 것을 설명할 때 사용하지 않는다.

  ```python
  x = 5	# This is an inline comment
  ```



#### 3\. Documentation Strings

`docstrings`은 함수나 클래스, 메서드, 모듈의 첫 번째 줄에서 (""")나 (''')으로 감싼 문자열들이다.

```python
def quadratic(a, b, c, x):
    """Solve quadratic equation via the quadratic formula.

    A quadratic equation has the following form:
    ax**2 + bx + c = 0

    There always two solutions to a quadratic equation: x_1 & x_2.
    """
    x_1 = (- b+(b**2-4*a*c)**(1/2)) / (2*a)
    x_2 = (- b-(b**2-4*a*c)**(1/2)) / (2*a)

    return x_1, x_2
```

- 한 줄의 docstrings는 """을 같은 줄에 놓는다.

  ```python
  def quadratic(a, b, c, x):
      """Use the quadratic formula"""
      x_1 = (- b+(b**2-4*a*c)**(1/2)) / (2*a)
      x_2 = (- b-(b**2-4*a*c)**(1/2)) / (2*a)
  
      return x_1, x_2
  ```




