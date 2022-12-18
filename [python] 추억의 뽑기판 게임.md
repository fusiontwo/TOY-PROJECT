---
layout: single
title: "[python] 추억의 뽑기판 게임"
---

# 1. 제작 동기   
학회를 구경하러 갔다가 기업 부스에서 추억의 뽑기판 게임을 해보았다. 정말 좋은 상품이 많았는데, 꽝을 뽑아서 매우 아쉬웠다. 프로그래밍으로 게임을 만들어서 여러 번 시도해보고, 당첨이 얼마나 어려운지 확인해보고 싶었다.   

# 2. 작성한 코드
```python
import numpy as np
import random

# 추억의 뽑기판을 출력한다. (번호 1~100)
print("===============추억의 뽑기판===============")
print((np.arange(100)+1).reshape(10, 10))
print("===========================================")

# random으로 6개의 번호를 선정하고, 배열 안의 순서대로 1~6등 당첨 번호로 정한다. 
win_numbers = np.random.randint(1, 101, size=(1, 6))
first_winner = win_numbers[0][0]
second_winner = win_numbers[0][1]
third_winner = win_numbers[0][2]
fourth_winner = win_numbers[0][3]
fifth_winner = win_numbers[0][4]
sixth_winner = win_numbers[0][5]

# 뽑기판 게임 참여자에게 번호를 1개 받는다.
choosed_number = int(input("원하는 번호를 뽑아보세요! "))
print(f"뽑으신 번호는 {choosed_number}입니다.")

# 고른 번호가 당첨 번호와 일치하면 등수와 상품을 출력한다.
if choosed_number == first_winner:
    print("1등 당첨입니다. 아이패드를 드립니다.")
elif choosed_number == second_winner:
    print("2등 당첨입니다. 무선 이어폰을 드립니다.")
elif choosed_number == third_winner:
    print("3등 당첨입니다. 영화 2인 티켓을 드립니다.")
elif choosed_number == fourth_winner:
    print("4등 당첨입니다. 텀블러를 드립니다.")
elif choosed_number == fifth_winner:
    print("5등 당첨입니다. 에코백을 드립니다.")
elif choosed_number == sixth_winner:
    print("6등 당첨입니다. 편의점 상품권 3000원을 드립니다.")
else:
    print("꽝! 아쉽지만 다음 기회에~")
```

# 3. 실행 결과
- 아래와 같이 참여자가 고른 번호와 랜덤으로 정해진 1~6등 당첨 번호 중 하나가 일치할 경우, 당첨되었다는 실행문을 출력한다.   
- 참여자가 고른 번호와 당첨 번호가 일치하지 않을 경우, 꽝을 출력한다.
![꽝](https://user-images.githubusercontent.com/101881124/208303888-9efe94fd-e48f-4f96-ba85-6026c0c73068.jpg)   
![5등 당첨](https://user-images.githubusercontent.com/101881124/208303897-20ff74fb-cb3f-4f51-81c8-62a7d9c69831.jpg)   
![6등 당첨](https://user-images.githubusercontent.com/101881124/208303900-48caa3f9-39e1-4050-bda1-99608f73558f.jpg)

# 4. 고찰
- choosed_number에 서로 다른 값을 20번 넣어보았다.   

|choosed_number|당첨 여부|
|:---:|:---:|
|10|꽝|
|20|꽝|
|30|꽝|
|40|꽝|
|50|꽝|
|65|꽝|
|77|꽝|
|6|꽝|
|43|꽝|
|18|꽝|
|79|꽝|
|45|꽝|
|17|꽝|
|58|꽝|
|36|3등 당첨|
|66|꽝|
|83|꽝|
|24|꽝|
|99|꽝|
|36|꽝|
![3등 당첨](https://user-images.githubusercontent.com/101881124/208304737-df457efe-ef9f-491d-87af-f5280af246e3.jpg)

- 100개의 번호 중 6개의 당첨 번호를 뽑을 확률은 0.06으로 매우 낮다. 20번이나 시도했으나, 그중에 1개가 당첨된 결과를 통해 낮은 확률을 느낄 수 있었다.   
- 표본이 20개로 매우 작아서 일반화하기에 부족하지만, 1/20 = 0.05로 이론상의 확률 0.06과 비슷했다.    
