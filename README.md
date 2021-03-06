# lazier

Lazier allows you to move faster when you are exploring how functions change with their input, this module was written because I often felt that there had to be an easier way to work in a interactive enviroment with jupyter notebooks.

Lazier allow you to create functions which remeber what their last inputs were.

## Installing 

```bash
pip install lazier
```
or
```bash
pip3 install lazier
```

## Demo

Me using it in [real life](https://arjunbazinga.github.io/lazier/softmax)  


### Mini demo
Without lazier:

```python
def foo(a,b,c,d):
    print(a)
    print(b)
    print(c)
    print(d)
```

```python
foo(a=1,b= 2, c=3, d=4)
```

    1
    2
    3
    4

```python
foo(d=2)
```

    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-3-9233fe4ac2c5> in <module>()
    ----> 1 foo(d=2)
    
    TypeError: foo() missing 3 required positional arguments: 'a', 'b', and 'c'



**with Lazier**:

```python
from lazier import lazier
```


```python
@lazier
def foo(a,b,c,d):
    print(a)
    print(b)
    print(c)
    print(d)
```


```python
foo(a=1,b= 2, c=3, d=4)
```

    1
    2
    3
    4


Now suppose you want to see how the output of the function changed if d was 7 in the above function call, with lazier it looks like:

```python
foo(d=7)
```

    1
    2
    3
    7


and so on.

```python
foo(a=9)
```

    9
    2
    3
    7



using reset you can forget all past values that it remebers

```python
foo.reset()
```


```python
foo()
```

    foo() missing 4 required positional arguments: 'a', 'b', 'c', and 'd'



```python
foo(a=1, b=11, c=3)
```

    foo() missing 1 required positional argument: 'd'



```python
foo(d=9)
```

    1
    11
    3
    9

