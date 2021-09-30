#### 05_data_structures

- 문자열 : `.find(x)` , `.index(x)`, `.replace(old, new[, count])`,  `.strip([chars])`, `.split([chars])`, `'separator'.join(iterable)`, `.captitalize()`, `.title()`, `.upper()`, `.lower()`, `.swapcase()`  

- 리스트 : `.append(x)`, `.extend(iterable)`, `.insert(i,x)`, `.remove(x)`, `.pop(i)`, `.clear()`, `.index(x)`, `.count(x)`, `.sort()`, `.reverse()` 

  - **List  Comprehension**

    ```python
    # 1. 세제곱 리스트
    cubic_list = [num**3 for num in range(1, 11)]
    
    # 2. 짝수만 담긴 리스트
    even_list = [num for num in range(1, 11) if num % 2 == 0]
    
    # 3. 곱집합
    pair = [(boy, girl) for boy in boys for girl in girls]
    
    # 4. 문자 제거하기
    result = ''.join(x for x in words if not x in vowels)
    ```

  - 순회 가능한(iterable) 데이터 구조에 적용 가능한 Built-in Function 

    - `map(function, iterable)`

      ```python
      # List comprehension
      new_numbers = [int(number) for number in numbers]
      
      # map
      new_numbers = list(map(int, numbers))
      ```

    - `filter(function, iterable)` : iterable에서 function 반환결과가 `True`인 것만 반환

    - `zip(*iterable)` 

      ```python
      girls = ['jane', 'ashley', 'mary']
      boys = ['justin', 'eric', 'david']
      pair = list(zip(girls, boys))
      ```

      > [('jane', 'justin'), ('ashley', 'eric'), ('mary', 'david')]

- 세트 : 변경 가능하고(mutable), 순서가 없고(unordered), 순회 가능한(iterable)

  `.add(elem)` , `.update(*others)`, `remove(elem)`, `.discard(elem)`, `.pop()`

- 딕셔너리 : 변경 가능하고(mutable), 순서가 없고(unordered), 순회 가능한(iterable)

  `.get(key[, default])`, `.pop(key[, default])`, `.update()`

  - Dictionary comprehension

    ```python
    # 1. key는 숫자, value는 key의 세제곱
    cubic_dict = {num: num**3 for num in range(1, 9)}
    
    # 2. if문 사용한 dict. comprehension
    even_dict = {num: num for num in range(1, 11) if num % 2 == 0}
    ```

  

#### 06_module

- 모듈 : 특정 기능을 `.py` 파일 단위로 작성한 것.

- 패키지 : **모듈들의 집합**. 패키지 안에는 또다른 서브 패키지를 포함 할 수도 있음

  > **`package.module` **을 사용하여 모듈을 구조화 한다.

- 다양한 모듈 사용법

  - 모듈

    ```python
    import module
    from module import var, fucntion, Class
    from module import *
    from module import fucntion as fun
    ```

  - 패키지

    ```python
    from package import module
    from pakage.moudle import var, function, Class
    ```

    

#### 07_OOP

- 객체

  - 파이썬에서 모든 것은 **`객체`**이고, **모든 `객체`는 특정 타입의 `인스턴스`**입니다.

  - **`속성`**은 객체의 상태/데이터를 뜻함.

    > <객체>.<속성>

  - **`메서드`**는 특정 객체에 적용할 수 있는 행위를 뜻함.

    > <객체>.<메서드>()

  - `class`는 객체들의 분류를 정의할 때 쓰이는 키워드

- 메서드 정의

  - `self `: 인스턴스 자신
    - 인스턴스 메서드는 호출 시 **첫번째 인자로 인스턴스 자신이 전달**
  - 생성자 메서드
    - 인스턴스 객체가 생성될 때 호출. `__init__`
  - 소멸자 메서드
    - 인스턴스 객체가 소멸되기 직전에 호출. `__del__`

- 메서드의 종류

  - 인스턴스 메서드
    - 인스턴스가 사용할 메서드
    - **호출시, 첫 번째 인자로 인스턴스 자기자신 self가 전달됨.**
  - 클래스 메서드
    - 클래스가 사용할 메서드
    - `@classmethod` 데코레이터를 사요하여 정의
    - **호출시, 첫 번째 인자로 클래스 `cls`가 전달됨.**
  - 스태틱 메서드
    - 클래스가 사용할 메서드
    - `@staticmethod`데코레이터를 사용하여 정의
    - **호출시, 어떠한 인자도 전달되지 않음**

- 상속

  > 클래스에서 가장 특징은 `상속`이다. 
  >
  > 부모 클래스의 모든 속성이 자식 클래스에게 상속 되므로 코드 재사용성이 높아짐.

  ``` python
  class ChildClass(ParentClass):
      <code block>
  ```

- super()

  - 자식 클래스에 메서드를 추가로 구현
  - 부모 클래스의 내용을 사용할 때, `super()`사용

  





















