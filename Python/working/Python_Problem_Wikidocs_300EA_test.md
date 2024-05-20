# 초보자를 위한 파이썬 300제
* source : https://wikidocs.net/book/922

## 파이썬 시작하기
* source : https://wikidocs.net/7014

### print 텝과 줄바꿈
*  exam : 005, 009


```python
print("안녕하세요.\n만나서\t\t반갑습니다.")  # \t 텝, \n 줄바꿈 의미
```


```python
print("first",end="");print("second")   # end='' print 함수는 두 번 사용한다. 세미콜론 (;)은 한줄에 여러 개의 명령을 작성하기 위해 사용한다.
```

### print 기초
* exam : 008, 004


```python
print("naver", "kakao", "sk", "samsung", sep="/")
```


```python
print('"C:\Windows"')
print('("C:\Windows")')
```

## 파이썬 변수
* source : https://wikidocs.net/7021

### type함수
* exam : 012, 015


```python
시가총액 = 298000000000000
현재가 = 50000
PER = 15.79

print(시가총액, type(시가총액))
print(현재가, type(현재가))
print(PER, type(PER))
```


```python
a = 128
print(type(a))
```


```python
a = "132"
print(type(a))
```

### 문자열, 정수, 실수 변환
* exam : 016, 017, 018, 019


```python
num_str = "720"
num_int = int(num_str)   # 문자열을 정수로 변환
print(num_int, type(num_int))
```


```python
num=100
result=str(num)    # 정수를 문자열 100으로 변환
print(result, type(result))
```


```python
a = "15.79"
b = float(a)    # 문자열을 실수로 변환
print(b,type(b))
```


```python
year = "2020"

print(int(year)-3)    #문자열을 정수로 변환
print(int(year)-2)
print(int(year)-1)
```

## 파이썬 문자열
*source : https://wikidocs.net/7022

### 문자열 슬라이싱
* exam : 022, 023, 024, 039


```python
license_plate = "24rk 2210"
print(license_plate[-4:])    # 음수 값은 문자열의 뒤에서부터 인덱싱 또는 슬라이싱함을 의미한다. 
```


```python
string = "홀짝홀짝홀짝"
print(string[::2])  # 슬라이싱할 떄 시작인덱스:끝인덱스:오프셋 을 지정할 수 있습니다.
```


```python
string = "PYTHON"
print(string[::-1])   # -1은 끝에서부터 라는 뜻...
```


```python
분기 = "2020/03(E) (IFRS연결)"
print(분기[:7])
```

### 문자열 인덱싱
* exam : 021


```python
letter = 'python'
print(letter[0], letter[2])
```

### 문자열 다루기

*exam : 025, 026, 027


```python
phone_number = "010-1111-2222"
phone_number = phone_number.replace("-"," ")
print(phone_number)
```


```python
phone_number = "010-1111-2222"
phone_number = phone_number.replace("-","")
print(phone_number)
```


```python
url = "http://sharebook.kr"
url_split = url.split('.')   # .을 기준으로 분리한다. 분리된 url 중 마지막을 인덱싱 하면 도메인만 출력 가능
print(url_split[-1])
```

### 문자열은  immutable (불변)
* exam : 028


```python
lang = 'python'
lang[0] = 'P'  #문자열은 수정할 수 없다. 실행 결과를 확인해보면 문자열이 할당(assignment) 메서드를 지원하지 않음을 알 수 있다.
print(lang)
```

### replace 메서드
* exam : 029, 030


```python
string = 'abcdfe2a354a32a'
string_replace = string.replace('a','A')
print(string_replace)
```


```python
string='abcd'
string.replace('b','B')
print(string)   # 문자열은 변경할 수 없는 자료형 이기 때문에 replace 매서드를 사용하면 원본은 그대로 둔채로 변경된 새로운 문자열 객체를 리턴해준다.
```

### Format String
* exam : 035, 036, 037


```python
#bad
name = 'python'

#print('이름: ' + name  + '나이: ' +3 )  --err!  print('이름: ' + name  + '나이: ' +str(3) ) -- ok
print('이름: ' , name  ,'나이: ' , 3 )
```


```python
#good (이 형태 평소에도 많이 씀)
print("이름: %s 나이: %d " % (name, 3))   # %s는 문자열 데이터 타입의 값을, %d는 정수형 데이터 타입 값의 출력을 의미
```


```python
name1 = "김민수" 
age1 = 10
name2 = "이철희"
age2 = 13
print("이름: {} 나이: {}".format(name1, age1))   # 문자열의 포맷 메서드는 타입과 상관없이 값이 출력될 위치에 {}를 적어주면 된다.
print("이름: {} 나이: {}".format(name2, age2))
```


```python
print(f"이름: {name1} 나이: {age1}")  # f-string은 문자열 앞에 f가 붙은 형태이다. f-string을 사용하면 {변수}와 같은 형탤호 문자열 사이에 타입과 상관없이 값을 출력 가능
print(f"이름: {name2} 나이: {age2}")
```

### strip 메서드
* exam : 040, 050


```python
data = "   삼성전자    "
data1 = data.strip()    #문자열에서  strip() 메서드를 사용하면 좌우의 공백을 제거할 수 있다. 이때 원본 문자열은 그대로 유지, 공백이 제거된 새로운 문자열 반환
print(data1)
```


```python
data = "039490     "   # rstrip() 메서드를 사용하면 오른쪽 고백이 제거된 새로운 문자열 객체가 반환
data = data.rstrip()
```

### split 메서드
* exam : 047, 048, 049


```python
a = "hello world"   # 문자열의 split() 메서드를 사용하면 문자열에서 공백을 기준으로 분리해준다.
a.split()
```


```python
ticker = "btc_krw"   # 문자열에서 split() 메서드는 문자열을 분리할 때 사용. 이때 어떤 값을 넘겨주면 그 값을 기준으로 문자열을 분리
ticker.split("_")
```


```python
date = "2020-05-01"
date.split("-")
```

## 파이썬 리스트
* source : https://wikidocs.net/7023

### 리스트 생성
* exam : 051


```python
movie_rank = ["닥터 스트레인지", "스플릿", "럭키"]
```

### 리스트 추가
* exam : 052, 053


```python
movie_rank.append("배트맨")
print(movie_rank)
```


```python
movie_rank = ["닥터 스트레인지", "스플릿", "럭키", " 배트맨"]
movie_rank.insert(1, "슈퍼맨")    # 리스트의 insert(인덱스,원소)  매서드를 사용하면 특정 위치에 값을 끼워넣기 할 수 있습니다.
print(movie_rank)
```

### 리스트의 최대값, 최소값
* exam : 057


```python
nums = [1, 2, 3, 4, 5, 6, 7]
print("max: ", max(nums))
print("min: ", min(nums))
```

### 리스트에 저장된 데이터의 갯수
* exam : 059


```python
cook = ["피자", "김밥", "만두", "양념치킨", "족발", "피자", "김치만두", "쫄면", "쏘세지", "라면", "팥빙수", "김치전"]
print(len(cook))   # len은 리스트에 저장된 데이터의 갯수를 구하는 함수이다.
```

### 리스트의 평균
* exam : 060


```python
nums = [1, 2, 3, 4, 5]
average = sum(nums) / len(nums)   # 리스트의 합을 리스트의 갯수로 나눠 평균을 구함
print(average)
```

### join 메서드
* exam : 066, 067, 068


```python
interest = ['삼성전자', 'LG전자', 'Naver', 'SK하이닉스', '미래에셋대우']
print(" ".join(interest))   # 한칸 띄우기
```


```python
print("/".join(interest))   # 중간에 / 넣기
```


```python
print("\n".join(interest))   # 줄바꿈하기
```

### 리스트 정렬
* exam : 070


```python
data = [2, 4, 3, 1, 5, 10, 9]
data.sort()    #sort  를 사용하면 오름차순 정렬가능
print(data)
```

## 파이썬 터플
* source : https://wikidocs.net/7027


```python
my_variable = ()
print(type(my_variable))
```

### 터플 오류
* 074


```python
t = (1, 2, 3)
t[0] = 'a'  # 터플은 원소의 값을 변경할 수 없다.

```

### 터플 -> 리스트 변환
* exam : 077


```python
interest = ('삼성전자', 'LG전자', 'SK Hynix')
data = list(interest)
print(data)
```

### 리스트 -> 터플 변환
* exam : 078


```python
interest = ['삼성전자', 'LG전자', 'SK Hynix']
data = tuple(interest)
print(data)
```

### range 함수
* exam : 080


```python
# 1~99까지의 정수 중 짝수만 저장된 튜플을 생성하라
data = tuple(range(2, 100, 2))
print( data )
```

## 파이썬 딕셔너리
* source : https://wikidocs.net/22000


```python
temp = { }
print(type(temp))
```

###딕셔너리 추가
*exam : 085, 086


```python
ice = {"메로나": 1000, "폴라포": 1200, "빵빠레": 1800}
print(ice)
```


```python
# 조스바 1200, 월드콘 1500 추가
ice = {"메로나": 1000, "폴라포": 1200, "빵빠레": 1800}
ice["죠스바"] = 1200
ice["월드콘"] = 1500
print(ice)
```

### 딕셔너리 사용하여 가격 출력, 수정, 삭제
* exam : 087, 088, 089


```python
# 가격출력
ice = {'메로나': 1000,
       '폴로포': 1200,
       '빵빠레': 1800,
       '죠스바': 1200,
       '월드콘': 1500}
print("메로나 가격: ", ice["메로나"])
```


```python
# 가격수정
ice = {'메로나': 1000,
       '폴로포': 1200,
       '빵빠레': 1800,
       '죠스바': 1200,
       '월드콘': 1500}
ice["메로나"] = 1300
print(ice)
```


```python
# 메로나 삭제
ice = {'메로나': 1000,
       '폴로포': 1200,
       '빵빠레': 1800,
       '죠스바': 1200,
       '월드콘': 1500}

del ice["메로나"]
print(ice)
```

### 딕셔너리 생성 및 인덱싱
*exam : 091, 092, 093, 094


```python
# 아이스크림 이름을 키값으로, (가격, 재고) 리스트를 딕셔너리의 값으로 저장
inventory = {"메로나": [300, 20], 
             "비비빅": [400, 3], 
             "죠스바": [250, 100]}
print(inventory)
```


```python
# 가격확인
print(inventory["메로나"][0], "원")
```


```python
# 재고확인
print(inventory["메로나"][1], "개")
```


```python
# 딕셔너리 추가
inventory = {"메로나": [300, 20],
              "비비빅": [400, 3],
              "죠스바": [250, 100]}
inventory["월드콘"] = [500, 7]
print(inventory)
```

###  딕셔너리 keys()매서드
* exam 095


```python
# 다음의 딕셔너리로부터 key 값으로만 구성된 리스트를 생성하라

icecream = {'탱크보이': 1200, '폴라포': 1200, '빵빠레': 1800, '월드콘': 1500, '메로나': 1000}
ice = list(icecream.keys())
print(ice)
```

## 파이썬 분기문
* source : https://wikidocs.net/7028


```python
if 4 < 3:
  print("Hello World.")
else:
  print("Hi, there.")
```


```python
# 사용자로부터 값을 입력받은 후 해당 값에 20을 더한 값을 출력하라. 
# 단 사용자가 입력한 값과 20을 더한 계산 값이 255를 초과하는 경우 255를 출력해야 한다.
# 입력값 : 200, 출력값 : 220
# 입력값 : 240, 출력값 : 255

user = input("입력값: ")
num = 20 + int(user)
if num > 255:
    print(255)
else:
    print(num)
```


```python
#사용자로부터 하나의 값을 입력받은 후 해당 값에 20을 뺀 값을 출력하라. 
# 단 출력 값의 범위는 0~255이다. 
# 예를 들어 결괏값이 0보다 작은 값이되는 경우 0을 출력하고 255보다 큰 값이 되는 경우 255를 출력해야 한다.

user = input("입력값: ")
num = int(user) - 20
if num > 255:
  print(255)
elif num < 0:
  print(0)
else:
  print(num)
```


```python
# 아래와 같이 fruit 딕셔너리가 정의되어 있다. 
# 사용자가 입력한 값이 딕셔너리 키 (key) 값에 포함되었다면 "정답입니다"를 아닐 경우 "오답입니다" 출력하라.

# >> 제가좋아하는계절은: 봄
# 정답입니다.

fruit = {"봄" : "딸기", "여름" : "토마토", "가을" : "사과"}
user = input ("제가가장좋아하는계절은: ")
if user in fruit:
  print("정답입니다.")
else:
  print("오답입니다.")
```


```python
# 아래와 같이 fruit 딕셔너리가 정의되어 있다. 
# 사용자가 입력한 값이 딕셔너리 값 (value)에 포함되었다면 "정답입니다"를 아닐 경우 "오답입니다" 출력하라.

# >> 좋아하는과일은? 한라봉
# 오답입니다.

fruit = {"봄" : "딸기", "여름" : "토마토", "가을" : "사과"}
user = input("좋아하는 과일은?")
if user in fruit.values():
  print("정답입니다.")
else:
  print("오답입니다.")
```

### 짝수/홀수 판별
* exam : 113


```python
user = input("")
if int(user) % 2 == 0:   # 전체를 2로 나누었을때 나머지가 0이면 짝수, 아니면 홀수 이기 때문이다.
  print("짝수")
else:
  print("홀수")
```

### 대문자 소문자 판별 및 변환
* exam : 121


```python
user = input("")
if user.islower():       #islower() 함수는 문자의 소문자 여부를 판별
    print(user.upper())  #upper() 함수는 대문자로, lower() 함수는 소문자로 변경
else:
    print(user.lower())
```

## 파이썬 반복문
* source : https://wikidocs.net/78562


```python
# 저장된 문자열의 길이를 다음과 같이 출력하라
# 리스트 = ["SK하이닉스", "삼성전자", "LG전자"]

#6
#4
#4

리스트 = ["SK하이닉스", "삼성전자", "LG전자"]
for 종목명 in 리스트:
  길이 = len(종목명)
  print(길이)
```


```python
리스트 = ['dog', 'cat', 'parrot']
for 이름 in 리스트:
  print(이름, len(이름))
```


```python
for 이름 in 리스트:
  print(이름[0])
```


```python
# for 문을 사용해서 반대로 출력하기
리스트 = ["가", "나", "다", "라"]

for 변수 in 리스트[::-1]:
  print(변수)
```

### for문을 사용해서 리스트의 음수 출력
* exam : 151


```python
리스트 = [3, -20, -3, 44]
for 변수 in 리스트:
  if  변수 < 0:
    print(변수)
```

### for 문을 사용해서 특정 배수 출력
* exam : 152, 153


```python
# 3의 배수만 출력
리스트 = [3, 100, 23, 44]
for 변수 in 리스트:
  if  변수 % 3 == 0:
    print(변수)
```


```python
#리스트에서 20 보다 작은 3의 배수를 출력하라
리스트 = [13, 21, 12, 14, 30, 18]
for 변수 in 리스트:
  if 변수 % 3 == 0:
    if 변수 < 20:
      print(변수)
```


```python
리스트 = [13, 21, 12, 14, 30, 18]
for 변수 in 리스트:
  if (변수 < 20) and (변수 %3 ==0):
    print(변수)
```

### for문 사용해서 대문자 판별
* exam : 155


```python
리스트 = ["A", "b", "c", "D"]
for 변수 in 리스트:
  if 변수.isupper():    #isupper()은 대문자 판별, islower()은 소문자 판별
    print(변수)
```


```python
리스트 = ["A", "b", "c", "D"]
for 변수 in 리스트:
  if not 변수.isupper(): #대문자 판별 함수 앞에 not 를 사용 가능
    print(변수)
```


```python
# 파일 이름이 저장된 리스트에서 확장자가 .h 인 파일 이름을 출력하라.
리스트 = ['intra.h', 'intra.c', 'define.h', 'run.py']
for 변수 in 리스트:
  split = 변수.split(".")
  if split[1] == "h":
    print(변수)
```


```python
# 파일 이름이 저장된 리스트에서 확장자가 .h나 .c인 파일을 화면에 출력하라.
리스트 = ['intra.h', 'intra.c', 'define.h', 'run.py']
for 변수 in 리스트:
  split = 변수.split(".")
  if (split[1] == "h") or (split[1] == "c"):
    print(변수)
```

### range 함수
* exam : 162, 164


```python
# 월드컵은 4년에 한 번 개최된다. range()를 사용하여 2002~2050년까지 중 월드컵이 개최되는 연도를 출력하라
# 참고 : range  3번째 파라미터는 증감폭을 결정합니다.

print (list(range(2002, 2051, 4)))
```


```python
for x in range(2002, 2051, 4):
  print(x)
```


```python
# 99부터 0까지 1씩 감소하는 숫자들을, 한 라인에 하나씩 출력하라.
for i in range(100):
  print(99-i)
```


```python
# 구구단 3단을 출력하라.
for i in range(1,10):
  print(3, "x", i, "=", 3 * i)
```


```python
# 구구단 3단을 출력하라. 단 홀수 번째만 출력한다.
num = 3
for i in range(1, 10, 2) :     # range 함수는 세번 째 파라미터는 증감폭을 결정한다.
    print (num, "x", i, " = ", num * i)
```

## 파이썬 함수
* source : https://wikidocs.net/23906


```python
# 두 개의 숫자를 입력받아 합/차/곱/나눗셈을 출력하는 print_arithmetic_operation 함수를 작성하라.

# print_arithmetic_operation(3, 4)
# 3 + 4 = 7
# 3 - 4 = -1
# 3 * 4 = 12
# 3 / 4 = 0.75

print_arithmetic_operation(3, 4)
def print_arithmetic_operation(a, b):
    print(a, "+", b, "=", a + b )
    print(a, "-", b, "=", a - b )
    print(a, "*", b, "=", a * b )
    print(a, "/", b, "=", a / b )
```


```python
# 하나의 리스트를 입력받아 짝수만 화면에 출력하는  print_even 함수를 정의하라
print_even ([1, 3, 2, 10, 12, 11, 15])
def print_even(my_list):
  for v in my_list:
    if v % 2 == 0:
      print(v)
```


```python
def 함수(num):
  return num+4

a = 함수(10)
b = 함수(a)
c = 함수(b)
print(c)
```
