# 초보자를 위한 파이썬 300제

https://wikidocs.net/book/922

## 01 파이썬 시작하기 (https://wikidocs.net/7014)

### 003 print 기초


```python
print('신씨가 소리질렀다. "도둑이야".')
```

### 004 print 기초


```python
print('"C:\Windows"')
```


```python
print('("C:\Windows")')
```

### 005 print 탭과 줄바꿈


```python
print("안녕하세요.\n만나서\t\t반갑습니다.")  # \t 텝, \n 줄바꿈 의미
```

### 007 print 기초


```python
print("naver", "kakao", "samsung", sep=";")  
# print  함수의  sep인자로 ";"를 입력하면 출력되는 값들 사이에 한칸의 공백대신 세미콜론이 출력된다.
```

### 008 print 기초


```python
print("naver", "kakao", "sk", "samsung", sep="/")
```

### 009 print 줄바꿈

다음 코드를 수정하여 줄바꿈이 없이 출력하세요. (힌트: end='') print 함수는 두 번 사용합니다. 세미콜론 (;)은 한줄에 여러 개의 명령을 작성하기 위해 사용합니다.

print("first");print("second")


```python
print("first",end="");print("second")
```

## 02. 파이썬 변수 (https://wikidocs.net/7021)

### 011 변수 사용하기


```python
삼성전자 = 50000
총평가금액 = 삼성전자 * 10
print(총평가금액)
```

012 변수 사용하기


```python
시가총액 = 298000000000000
현재가 = 50000
PER = 15.79

print(시가총액, type(시가총액))
print(현재가, type(현재가))
print(PER, type(PER))
```

### 015 type 함수


```python
a = 128
print(type(a))
```


```python
a = "132"
print(type(a))
```

### 016 문자열을 정수로 변환


```python
num_str = "720"
num_int = int(num_str)
print(num_int, type(num_int))
```

### 017 정수를 문자열 100으로 변환


```python
num=100
result=str(num)
print(result, type(result))
```

### 018 문자열을 실수로 변환


```python
a = "15.79"
b = float(a)
print(b,type(b))
```

### 019 문자열을 정수로 변환


```python
year = "2020"

print(int(year)-3)
print(int(year)-2)
print(int(year)-1)
```

### 020 파이썬 계산


```python
a = 48584
b = 36
print(a*b)
```


```python
월 = 48584
총금액 = 월 * 36
print(총금액)
```

## 파이썬 문자열 (https://wikidocs.net/7022)


```python

```
