```



```

# Numpy
Numpy
- 수치 데이터를 다루는 파이썬 패키지, 다차원 배열을 효과적으로 처리
- 다차원 배열을 효과적으로 처리할 수 있도록 도와주는 도구
- 단일 자료형만 저장 가능하므로 속도나 메모리 효율성이 좋다
- 데이터 분석 및 ML/DL에서 많이 사용

Numpy 학습 내용
- 차원: 1차원 - 행, vector / 2차원 - 행열, Matrix / 3차원 - 행열면, 채널, Tensor / n차원 - nTensor
- 사용법: 배열 초기화, 인덱싱&슬라이싱, 배열결합, 배열분할, 배열형태 바꾸기
- 연산: 기본 연산, 브로드캐스팅, 다양한 집계함수
- 파일: 읽고 저장

Numpy 설치/실행
- 설치: %pip install numpy
- 실행: import numpy as np

## 배열 초기화
### list 초기화
- 1차원 배열
- 2차원 배열
- 3차원 배열

my_list=[1, 2, 3]
my_arr=np.array(my_list)

@배열 출력
print(my_arr)
[1 2 3]

@배열 인덱스
print(my_arr[2])
3

@데이터 사이즈
print(my_arr.size)
3

@데이터 차원의 크기
print(my_arr.shape)
(3, )

@배열의 원소 타입
print(my_arr.dtype)
int64

@배열 출력2
arr=np.array([[5, 9, 10, 3, 1], 
                [8, 3, 4, 2, 5]])
arr[1][2] >> arr 배열의 두 번째 행, 세 번째 열에 있는 요소
4

@배열의 차원의 크기
arr.shape
(2, 5) >> (행, 열) >> 행 2개 열 5개

@ 배열의 크기
arr.size
10 >> 2*5=10

@ 배열의 원소 타입
int64


### 자주 사용하는 함수
num=np.array([1, 1, 2, 3, 3, 3, 1])
print("중복값 제거", np.unique(num))

copy_num=num.copy()
print("배열 복사:", copy_num)

num.sort()
print("오름차순:", num)
print("내림차순:", num[::-1])
 >> sort로 오름차순 정렬 후 ::-1로 역순으로 뒤집기

중복값 제거 [1 2 3]
배열 복사: [1 1 2 3 3 3 1]
오름차순: [1 1 1 2 3 3 3]
내림차순: [3 3 3 2 1 1 1]

arr.sort(axis=1)
print("행기준 정렬\n", arr)
행기준 정렬
 [[ 1  3  5  9 10]
 [ 2  3  4  5  8]]

 >> 2차원 배열에서
 axis=0: 열을 따라 연산을 수행
axis=1: 행을 따라 연산을 수행

>> 3차원 배열에서
axis=0: 가장 바깥쪽 축을 따라 연산을 수행 (깊이)
axis=1: 두 번째 축을 따라 연산을 수행(행)
axis=2: 가장 안쪽 축을 따라 연산을 수행합니다. (열)