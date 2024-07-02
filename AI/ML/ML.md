# Machine Learning
> 인공지능의 한 분야, 실험적으로 얻은 Data로부터 점점 개선되도록 할 수 있는 알고리즘을 설계하고 개발하는 분야이다.

### 프로그래밍과 기계학습의 차이
![alt text](/Image/ML/machine%20learning.png)
### 기계학습의 중요한 개념과 목표
>가장 큰 목표는 'Generalization : 일반화' 이다.

## 일반화
일반화의 정의
- 특정한 공통 속성이 있는 추상화 형태이다.
- 세 살짜리 아이는 태어나서 수 많은 나무를 보게되는데 이들 사이에 일종의 유사성을 판단해서 전형을 만든다. 이런식으로 일반화를 하게된다. (추상화 과정)

학습목표
- Training data로부터 어떤 패턴을 배워서 우리가 Training data에서 보지못한 새로운 Data가 오더라도 잘하길 기대하는 것이다.

## No Free Lunch Theorem for ML
- 어떤 기계학습 알고리즘도 다른 기계학습 알고리즘보다 더 좋다고는 할 수 없는 것이다.
- 매번 새로운 Task, 혹은 새로운 Data를 모을 때마다 최적의 알고리즘을 찾는 과정을 수행해야한다.

## 기계학습의 종류
1. 감독학습, 지도학습 Supervised learning
2. 비감독학습, 비지도학습 Unsupervised learning
3. 준지도학습 Semi-supervised learning
4. 강화학습 Reinforcement learning

### Supervised learning
Input, Output을 쌍으로 만들고 그런 학습 Data로 기계학습 알고리즘를 학습한다.

![alt text](/Image/ML/supervised%20learning.png)

### Unsupervised learning
학습 Data가 x로만 구성돼 있다.
비지도학습의 경우에는 x만 주고 알려준게 없기 때문에 너무 큰 기대를 하면 안된다.
![alt text](/Image/ML/unsupervised%20learning.png)

### Semi-supervised learning
Supervised learning 과 Unsupervised learning의 중간에 위치한다.
학습데이터를 줄 때 몇몇 Data는 x, y를 주고 몇몇 Data는 x만 준다.
- LU learning : 몇몇의 Data들은 Lable을 주고 그이외의 Data들은 Label을 주지 않는 경우
- PU learning : 특정 class에 대해서만 Data가 주어지고, 그외 class는 Data를 주지 않는 경우

Semi-supervised learning은 검은색 Data와 같이 Label이 안 주어진 Unlabel 된 Data에게 Label 을 확률적으로 줄 수 있다.
![alt text](/Image/ML/semi-supeervised%20learning.png)

### Reinforcement learning
Dataset이 사전에 주어진게 아니라 환경이 주어져있다. 환경이랑 Interaction을 하면서 학습을 하는 과정이다.

![alt text](/Image/ML/reinforcement%20learning.png)