---
title:  "[LinearRegression(1)]"
excerpt: " "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
 
date: 2025-04-10
last_modified_at: 2025-04-10
---


# 물고기 무게 예측측

```py
# 필수 라이브러리 import (NumPy, Pandas, 시각화 등)
import numpy as np
import pandas as pd
import seaborn as sns  

# 그래프 한글 설정
import matplotlib.pyplot as plt   
import matplotlib as mpl          
mpl.rc('font', family='Malgun Gothic ')     
plt.rcParams['axes.unicode_minus']=False

# 머신러닝 관련 모듈 import (scikit-learn)
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
```

```py
# 물고기의 길이와 무게 데이터 입력해주기! (가상의 데이터임.)

perch_length=np.array([8.4, 13.7, 15.0, 16.2, 17.4, 18.0, 18.7, 19.0, 19.6, 20.0,
                     21.0, 21.0, 21.0, 21.3, 22.0, 22.0, 22.0, 22.0, 22.0, 22.5,
                     22.5, 22.7, 23.0, 23.5, 24.0, 24.0, 24.6, 25.0, 25.6, 26.5,
                     27.3, 27.5, 27.5, 27.5, 28.0, 28.7, 30.0, 32.8, 34.5, 35.0,
                     36.5, 36.0, 37.0, 37.0, 39.0, 39.0, 39.0, 40.0, 40.0, 40.0,
                     40.0, 42.0, 43.0, 43.0, 43.5, 44.0]) 


perch_weight=np.array([5.9, 32.0, 40.0, 51.5, 70.0, 100.0, 78.0, 80.0, 85.0, 85.0,
                     110.0, 115.0, 125.0, 130.0, 120.0, 120.0, 130.0, 135.0, 110.0,
                     130.0, 150.0, 145.0, 150.0, 170.0, 225.0, 145.0, 188.0, 180.0,
                     197.0, 218.0, 300.0, 260.0, 265.0, 250.0, 250.0, 300.0, 320.0,
                     514.0, 556.0, 840.0, 685.0, 700.0, 700.0, 690.0, 900.0, 650.0,
                     820.0, 850.0, 900.0, 1015.0, 820.0, 1100.0, 1000.0, 1100.0,
                     1000.0, 1000.0]) 

# 길이 데이터 개수와 무게 데이터 개수 확인. -> why needed? 입력 데이터(X)와 정답 데이터(Y)의 개수가 같아야 함

perch_length.shape, perch_weight.shape
```

---
다음으로 넘어가기에 앞서, train_test_split() 함수와 2차원 변환에 대해 알아보자.

(1) train_test_split() 함수
1. 주어진 데이터를 섞고 자동으로 나눠준다(scikit-learn 라이브러리에서 제공하는 모듈이다.)
2. default : 75% 학습용 / 25% 테스트용
    ** 참고로 비율을 다르게 하고 싶다면 test_size를 적어주면 된다. 
        ex, train_test_split(X, y, test_size=0.2, random_state=42)
       
       비율은 데이터가 크면 test_size = 0.2 ~ 0.3을 사용한다.
3. 1번에서 데이터를 섞는다고 하였는데, 이때 데이터는 무작위로 섞인다. 따라서 그 값을 고정해주기 위해 random_state를 쓴다.

(2) 2차원 변환
사이킷런(Sklearn)의 머신러닝 모델들은 **입력 데이터 X는 항상 2차원 배열(행렬)**을 원함.
(변환 전) X_train = [8.4, 13.7, 15.0, ...]  # shape: (42,) → 1차원
(변환 후) X_train = [[8.4], [13.7], [15.0], ...]  # shape: (42, 1) → 2차원
---

```py
# 전체 데이터를 학습용(X_train, y_train) 과 테스트용(X_test, y_test) 으로 나눠줌.
X_train, X_test, Y_train, Y_test=train_test_split(perch_length, perch_weight, random_state=42)

# 2차원 변환 및 확인
X_train=X_train.reshape(-1, 1)
X_test=X_test.reshape(-1, 1)
X_train.shape, X_test.shape
```
