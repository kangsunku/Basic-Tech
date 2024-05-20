# Markdown
## Markdown(마크다운이란?)
- 마크다운은 글자에 서식을 적용하는 또 다른 방법
- 아주 쉬우며 본문의 가독성 또한 좋음
- [Markdown 문법,사용법,에디터](http://sergeswin.com/1013)
- [MarkDown 사용법 총정리](https://heropy.blog/2017/09/30/markdown/)

## MarkDown Syntax Example
```
<http://chenluois.com>,
[Mou](https://twitter.com/mou)
[a relative link](other_file.md)
![Smaller icon](http://25.io/smaller/favicon.ico "Title here")
[^1]: And that's the footnote.
Name         | Value                          | Desc
-------------|--------------------------------|-------
             |                                |
```

# Editor
## Web Editor
- <https://stackedit.io/>

## Application
### Mou
## Editor Plugin
### Atom
### Sublime

# Syntax
## 제목(Header)
```
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6

제목 1
======

제목 2
------

```
## 강조(Emphasis)
- _이텔릭체_ :  _
```
  _언더바(underscore)_
```

- **두껍게** __두껍게__ : ** or __
```
  **별표(asterisks)**
  __언더바(underscore)__
```
-"** _이텔릭체_ 와 두껍게**를 같이 사용할 수 있습니다."

- ~~취소선~~ : ~~
```
  ~~물결표시(tilde)~~
```
- `밑줄` : `
```
  <u>밑줄</u>은 `<u></u>`를 사용하세요.
```

## 순서
```
1. 순서가 필요한 목록
1. 순서가 필요한 목록
  - 순서가 필요하지 않은 목록(서브)
  - 순서가 필요하지 않은 목록(서브)
1. 순서가 필요한 목록
  1. 순서가 필요한 목록(서브)
  1. 순서가 필요한 목록(서브)
1. 순서가 필요한 목록

- 순서가 필요하지 않은 목록에 사용 가능한 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)
```

## 수식
* Example
```
\begin{equation}
Z = \frac{X - \mu  }{ \sigma }
\end{equation}
```

## Link + image
[![finfra](http://finfra.com/f/f.png)](http://finfra.com)
```
[![finfra](http://finfra.com/f/f.png)](http://finfra.com)
```

## 표

| 값 | 의미 | 기본값 |
|----|:---:|---:|
| 'static' | 유형(기준) 없음 / 배치 불가능 | 'static' |
```
| 값 | 의미 | 기본값 |
|----|:---:|---:|
| 'static' | 유형(기준) 없음 / 배치 불가능 | 'static' |
```

# 주석
> 콜론을 입력하면 원하는 위치로 정렬 가능
>> 콜론을 입력하면 원하는 위치로 정렬 가능
```
> 콜론을 입력하면 원하는 위치로 정렬 가능
>> 콜론을 입력하면 원하는 위치로 정렬 가능
```
