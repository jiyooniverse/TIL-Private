## decorator 함수



```python
def hello(func):
    def wrapper():
        print('hi!')
        func()
        print('python')
    return wrapper


@hello
def bye():
    print('bye!')
    
    
bye()
```

>hi!
>
>bye!
>
>python