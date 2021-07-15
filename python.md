# 07_14 파이썬 학습내용 정리

## 기초

```python
print('hi!') # 기본적인 출력문
a = "안녕하세요 행운의 봇이에오"  # 변수 입력 방법

```

## 리스트

```python
lunch_box = ['순대국밥', '김밥', '떡라면', '짜장면']
print(lunch_box)   # 전체 출력
print(lunch_box[1])  # '김밥' 출력
```

## 딕셔너리

> 기본적으로 key : value 의 구조를 갖고 {}를 사용한 리스트

```python
phone_book = {'친구1' : '010-5555-8888', '친구2' : '010-4852-4821', '친구3' : '010-9787-2734'}
print(phone_book['친구1']) # 친구1의 value 출력
print(phone_book.keys())  # 딕셔너리의 key값 출력
```

## 조건(if)문

> 조건을 설정하고 조건에 맞는 형식을 찾아 값을 반환함. 기본 구조는 `if` `else` 의 구조이고, 다조건문에는 `elif`를 사용하여 조건문 구조 취함.

```python
if dust > 150:
  print("매우나쁨")
elif dust > 80 and dust <= 150:
  print("나쁨")
elif dust <= 80 and dust > 30:
  print("보통")
else:
  print("좋음")
```



## 반복문

>반복문에는 while문과 for문이 있음. 모두 조건을 설정하고 그것을 반복작업하는 구조.
>
>

### while문

```python
a = "안녕하세요 행운의 봇이에오"
n = 0
while n < 3:
  print(a)
  n = n + 1
```

### for문

```python
 # 반복문 for문
'''
정해진 것을 반복!
정해진 것을 만들어야만 한다...
길이가 3이여야한다. (총 3번이니까)
'''
for i in range(3):
  print('hi!')

# 리스트를 모두 반복하는 법(for)
lunch_box = ['햄버거', '피자', '치킨']

# 1) lunch_box를 다 돌기
for lunch in lunch_box:
  # lunch = ....
  print(lunch)

# 2) lunch_box의 길이를 바탕으로 0부터 하나씩 접근하기
for i in range(len(lunch_box)):
  print(lunch_box[i]
```



## Random 값 출력

> random을 사용하기 위해서는 `모듈`이라는 파이썬의 함수 패키지를 사용해야 한다. 그것을 하는 방법은
>
> `import modulename` 의 형식을 취한다.

```python
import random

# random.sample을 사용한 6개의 번호 임의 추출
menu2 = range(1, 46)
lucky = random.sample(menu2, 6)
print(lucky) 

# random.choice를 사용한 1개의 값 임의 추출
import random


lunch_box = ['순대국밥', '김밥', '떡라면', '짜장면']

choice = random.choice(lunch_box)
print("{0} 드세요".format(choice))
```



# 07_15 파이썬 정리

## 데이터 크롤링

>웹페이지를 가져와서 데이터를 추출하는 방식
>
>ex) 네이버 금융 코스피 지수 추출하기

```python
import requests   # 데이터를 추출하기 위해 필요한 모듈
from bs4 import BeautifulSoup  


url = "https://finance.naver.com/sise/"

response = requests.get(url).text
# print(response)

# 텍스트에서 정보를 추출
data = BeautifulSoup(response)
# 선택지를 활용해서 해당 위치를 찾는다
kospy = data.select_one('#KOSPI_now')
# 출력
print(kospy.text)
```



ex2) 미국 환율정보 추출하기

```python
import requests
from bs4 import BeautifulSoup


url = 'https://finance.naver.com/marketindex/'

response = requests.get(url).text
# print(response)

# 텍스트에서 정보를 추출
data = BeautifulSoup(response, 'html.parser')
# 선택지를 활용해서 해당 위치를 찾는다
exchange_rate = data.select_one('#exchangeList > li > a.head.usd').text
# 출력
# f-string : 파이썬 3.6 이상에서만 동작
print(f'달러 환율은 {exchange_rate} 입니다.')
```



## API 추출

> API란? 크롤링이 웹페이지에서 데이터를 추출해오는 것이라면, API는 웹페이지를 그대로 받아와 데이터를 사용하는 개념이라고 할 수 있다.

ex) age따오기

```python
import requests

# 무식한 방식
url = ["https://api.agify.io?name=tak",
       "https://api.agify.io?name=tony",
       "https://api.agify.io?name=eric",
       "https://api.agify.io?name=musk"]

response = [requests.get(url[0]).json(),
            requests.get(url[1]).json(),
            requests.get(url[2]).json(),
            requests.get(url[3]).json()]
for i in range(0, 4):
    print(response[i]['age'])
    
# 세련된 방식
names = ['tak', 'tony', 'tom', 'ann', 'eric', 'musk']
for name in names:
    url1 = f'https://api.agify.io?name={name}'
    response = requests.get(url1)
    result = response.json()
    print(result['age'])

```



ex) 국가 따오기

```python
import requests

names = ['michael', 'tom', 'henry', 'chris']
for name in names:
    url = f"https://api.nationalize.io?name={name}"
    response = requests.get(url).json()
    print(response['country'][0]['country_id'])

```



