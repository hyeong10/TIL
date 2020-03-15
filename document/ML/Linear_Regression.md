# Linear Regression

- 어떤 문제의 답을 예상할 때, 일종의 규칙(함수)가 있다고 생각하여 이를 유추하는 과정
- Linear Regression은 일종의 선형 함수를 찾아가는 과정

```
f(x) = wx + b
```
> w와 b를 찾아가는 과정

- 실제 데이터의 결과와 수식을 돌려나온 결과의 차이를 줄여나가면서 조정
- 이때 사용하는 함수를 Cost Function(Loss Function)라 칭함
- 얘를 들어 선형함수의 가장 간단한 Cost Function은 결과값 사이의 거리

```
((wx+b) - Y)^2
```
> wx+b는 수식을 돌려나온 결과, Y는 실제 결과

- 이러한 오차를 줄이기 위해 gradient decent 사용
