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

### 021 문자열 인덱싱


```python
letter = 'python'
print(letter[0], letter[2])
```

### 022 문자열 슬라이싱


```python
license_plate = "24rk 2210"
print(license_plate[-4:])    # 음수 값은 문자열의 뒤에서부터 인덱싱 또는 슬라이싱함을 의미한다. 
```

### 023 문자열 인덱싱 ???


```python
string = "홀짝홀짝홀짝"
# 실행예 : 홀홀홀
print(string[::2])  # 슬라이싱할 떄 시작인덱스:끝인덱스:오프셋 을 지정할 수 있습니다.
```

### 024 문자열 슬라이싱


```python
string = "PYTHON"
print(string[::-1])   # -1은 끝에서부터 라는 뜻...
```

### 025  문자열 치환


```python
phone_number = "010-1111-2222"
phone_number = phone_number.replace("-"," ")
print(phone_number)
```

### 026 문자열 다루기 (025번 문제 이어서)


```python
phone_number = "010-1111-2222"
phone_number = phone_number.replace("-","")
print(phone_number)
```

### 027 문자열 다루기


```python
url = "http://sharebook.kr"
print(url[-2]+url[-1])   
```


```python
url = "http://sharebook.kr"
url_split = url.split('.')   # .을 기준으로 분리한다. 분리된 url 중 마지막을 인덱싱 하면 도메인만 출력 가능
print(url_split[-1])
```

### 028 문자열은 immutable


```python
lang = 'python'
lang[0] = 'P'  #문자열은 수정할 수 없다. 실행 결과를 확인해보면 문자열이 할당(assignment) 메서드를 지원하지 않음을 알 수 있다.
print(lang)
```

### 029 replace 메서드


```python
string = 'abcdfe2a354a32a'
string_replace = string.replace('a','A')
print(string_replace)
```

### 030 replace 메서드


```python
string='abcd'
string.replace('b','B')
print(string)   # 문자열은 변경할 수 없는 자료형 이기 때문에 replace 매서드를 사용하면 원본은 그대로 둔채로 변경된 새로운 문자열 객체를 리턴해준다.
```

### 031 문자열 합치기


```python
a = "3"
b = "4"
print(a+b)
```

### 문자열 곱하기


```python
print("Hi" *3)

```

### Format String


```python
#bad
name = 'python'

print('이름: ' + name  + '나이: ' +3 )

```


```python
print("이름: %s 나이: %d " % ('name', 3))   # %s는 문자열 데이터 타입의 값을, %d는 정수형 데이터 타입 값의 출력을 의미

```


```python

```
