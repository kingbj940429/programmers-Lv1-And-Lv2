# 목차

1) [소수찾기 Lv1 ](#소수찾기-Lv1)
2) [시저암호 Lv1 ](#시저암호-Lv1)

# 문제

## 소수찾기 Lv1

**에라토스테네스의 체** 를 이용하여야 시간 초과에 걸리지 않는다.

### 오답

시간초과에 걸린다..

```python
def solution(n):
    s = 0
    sum = 0
    for i in range(2,n+1): 
        for j in range(2,i): 
            if i%j == 0: 
                s += 1 
        if s == 0: 
            sum += 1 
        s = 0 
    return sum 
```

### 정답
```python
def solution(n):
    a = set([i for i in range(3,n+1,2)])
    for i in range(3, n+1, 2):
        if(i in a):
            a -=  set([i for i in range(i*2,n+1,i)])# a = a - set 이런식으로 하면 시간초과에 걸린다
    
    return len(a) + 1
```

## 시저암호 Lv1

### 정답

**chr()** => 아스키를 문자로, 

**ord()** => 문자를 아스키로,

```python
def solution(s, n):
    s_list = list(s)
    datas = []
    for k in s_list :
        if(k.isupper()):
            result = chr((ord(k)-ord('A')+n)%26 + ord('A'))
        elif(k.islower()):
            result = chr((ord(k)-ord('a')+n)%26 + ord('a'))
        if(k == ' '):
            datas.append(' ') 
        else:
            datas.append(result)
    return ''.join(datas)
```
