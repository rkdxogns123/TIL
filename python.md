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

