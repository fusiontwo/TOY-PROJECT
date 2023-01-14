---
layout: single
title: "[python] 미니게임기 (가위바위보, 참참참, 우유 마시기)"
---

# 1. 제작 동기
다양한 경우의 수를 고려하는 연습을 하고 싶었다. 게임을 만들 때는 사용자의 입력과 게임 내부의 다양한 상황에 따라 매우 다양한 경우의 수를 고민하게 되므로, 유익할 것이라고 생각했다. 게임 1개만 있으면 심심하니까, def()를 활용하여 3개의 게임이 있는 게임기를 만들었다. 간단하게 할 수 있는 가위바위보나 참참참, 조금은 특이한 우유 빨리 마시기 게임도 추가했다. 예전에 학교 축제에 우유 빨리 마시기 대회가 있었다고 하여 게임으로 각색해보았다.   

# 2. 작성한 코드
```python
# 심심할 때 언제든지! 재밌는 미니 게임기!
# 게임 종류 : 가위바위보, 참참참, 우유 빨리 마시기

# Game1. 가위바위보
import random
def RSP():
    print("""
==============================
| 가위를 내려면 S,           |
| 바위를 내려면 R,           |
| 보를 내려면 P를 입력하세요.|
==============================
          """)

    user = input("안 내면 진다 가위바위보! : ")
    string = "RSP"
    computer = random.choice(string)
    if (user == "R" and computer == "R") or (user == "S" and computer == "S") or (user == "P" and computer == "P"):
        print(f"컴퓨터는 {computer}!")
        print("비겼습니다. 한 판 더!")
    elif (user == "R" and computer == "S") or (user == "S" and computer == "P") or (user == "P" and computer == "R"):
        print(f"컴퓨터는 {computer}!")
        print("이겼습니다!!^_^")        
    elif (user == "R" and computer == "P") or (user == "S" and computer == "R") or (user == "P" and computer == "S"):
        print(f"컴퓨터는 {computer}!")
        print("졌습니다. 다음 판에는 이겨봅시다!")  
    else:
        print("R 또는 S 또는 P 중 하나를 입력해주세요.")    

# Game2. 참참참
def Cham():
    print("""
============================================
| 오른쪽으로 고개를 돌리려면 R을,          |
| 왼쪽으로 고개를 돌리려면 L을 입력하세요. |   
============================================
          """)
    user_direction = input("고개를 돌릴 방향을 선택하세요. : ")
    direction ="RL"
    computer_direction = random.choice(direction)
    if user_direction == computer_direction:
        print(f"컴퓨터는 {computer_direction}!")
        print("딱 걸렸어요! 졌습니다.")
    elif (user_direction == 'R' and computer_direction == 'L') or (user_direction == 'L' and computer_direction == 'R'):
        print(f"컴퓨터는 {computer_direction}!")
        print("잘 피하는데요? 이겼습니다!^_^")
    else:
        print("R과 L만 입력 가능합니다.")

# Game3. 우유 빨리 마시기
import time
def Milk():
    print("""
========================================================================
| 정말 많은 개수의 50ml 잔에 건국 우유를 나누어 담아놓았습니다!        |
| 랜덤으로 주어지는 숫자보다 많은 잔의 우유를 다 마시면 이기는거에요!! |
| 제한된 시간은 10초! 알파벳 milk 단어 하나는, 우유 한 잔 마신겁니다.  | 
| (milk를 입력하고, 입력이 끝나면 꼭 엔터를 누르세요.)                 |
========================================================================    
        """)

    goal_num = random.randint(3,10)
    start = time.time() # 시작
    num_cup = input(f"10초 동안 우유 {goal_num}잔 마시기! ").count('milk')
    print(f"{time.time()-start:.4f} sec")
    if (num_cup >= goal_num) and time.time()-start <= 10 :
        print(f"성공입니다. 우유를 {time.time()-start:.4f}초 동안 {num_cup}잔 마셨습니다.")
    else :
        print(f"실패입니다. 우유를 {time.time()-start:.4f}초 동안 {num_cup}잔 마셨습니다.")
    

# 원하는 게임 종류 입력받기
while True:
    game = input("""
* 게임의 룰을 미리 숙지하세요 *
==============================
| 가위를 내려면 S,           |
| 바위를 내려면 R,           |
| 보를 내려면 P를 입력하세요.|
==============================
============================================
| 오른쪽으로 고개를 돌리려면 R을,          |
| 왼쪽으로 고개를 돌리려면 L을 입력하세요. |   
============================================
========================================================================
| 정말 많은 개수의 50ml 잔에 건국 우유를 나누어 담아놓았습니다!        |
| 랜덤으로 주어지는 숫자보다 많은 잔의 우유를 다 마시면 이기는거에요!! |
| 제한된 시간은 10초! 알파벳 milk 단어 하나는, 우유 한 잔 마신겁니다.  | 
| (milk를 입력하고, 입력이 끝나면 꼭 엔터를 누르세요.)                 |
======================================================================== 
원하는 게임을 입력하세요. (가위바위보 / 참참참 / 우유 빨리 마시기)
종료하고 싶으면 '종료'를 입력하세요.
게임 이름: """)
    if game == "가위바위보":
        RSP()
    elif game == "참참참":
        Cham()
    elif game == "우유 빨리 마시기":
        Milk()
    elif game == "종료":
        break
    else:
        print("정확한 게임 이름을 입력해주세요.")
```

# 3. 실행 결과
- 미니 게임기를 실행하면 게임 3개의 룰과 원하는 게임 이름을 입력하는 칸이 나타난다.   
![미니게임기 실행1](https://user-images.githubusercontent.com/101881124/212482287-b0d855aa-6feb-4cef-8c32-bc6b6c6cb5ce.jpg)   
- 가위바위보 게임에서는 사용자에게 입력받은 R 또는 S 또는 P와 컴퓨터에 랜덤으로 할당된 R 또는 S 또는 P에 따라 이기거나 비기거나 지는 상황이 발생한다.   
![미니게임기 실행2 가위바위보 이김](https://user-images.githubusercontent.com/101881124/212482408-053c20fe-85ab-4b53-95b6-d6072087c7ea.jpg)
![미니게임기 실행3 가위바위보 비김](https://user-images.githubusercontent.com/101881124/212482424-cc436e74-90a5-441d-a3a5-e9a5ea8c58a1.jpg)
![미니게임기 실행4 가위바위보 짐](https://user-images.githubusercontent.com/101881124/212482427-212efa93-7dd3-4820-ac0f-0cb4cb7d261a.jpg)
- 참참참 게임에서는 사용자에게 입력받은 R 또는 L과 컴퓨터에 랜덤으로 할당된 R 또는 L에 따라 이기거나 지는 상황이 발생한다.   
![미니게임기 실행6 참참참 이김](https://user-images.githubusercontent.com/101881124/212482530-dbf6c2a1-05ae-4844-9cbb-fc8c406f3482.jpg)
![미니게임기 실행5 참참참 짐](https://user-images.githubusercontent.com/101881124/212482531-2f4f6d6b-199d-4ab2-8d5e-edff592b0912.jpg)
- 우유 마시기 게임에서는 10초 이하의 시간과 랜덤으로 주어진 잔 수 이상으로 'milk'를 입력해야 게임에서 이긴다.
![미니게임기 실행9 우유마시기 시간충족,횟수충족](https://user-images.githubusercontent.com/101881124/212482629-55bdce84-c4e6-48eb-bb98-8939cbca4597.jpg)
- 우유 마시기 게임에서 시간은 충족했는데 잔 수를 불충족했거나, 잔 수는 충족했는데 시간을 불충족했거나, 시간과 잔 수 모두를 불충족하는 경우는 모두 지는 것이다.   
![미니게임기 실행7 우유마시기 시간충족,횟수불충족](https://user-images.githubusercontent.com/101881124/212482872-d3008fe6-4652-4a2b-ae5e-42edab869185.jpg)
![미니게임기 실행8 우유마시기 시간불충족,횟수충족](https://user-images.githubusercontent.com/101881124/212482877-efb00a11-4dfb-41e5-9321-3dada312978d.jpg)
![미니게임기 실행10 우유마시기 시간불충족,횟수불충족](https://user-images.githubusercontent.com/101881124/212482889-3615b4d9-1505-422e-9db7-57aa4f688e46.jpg)
- 게임 이름 대신 '종료'를 입력하면 while문이 더 이상 반복되지 않아서 게임기 작동이 중단된다.   
 ![미니게임기 실행11 종료](https://user-images.githubusercontent.com/101881124/212482910-2fa4bab4-5d88-4794-ba1e-2fff91912b9f.jpg)
- 게임 이름을 입력할 때와 각 게임 실행 후에 사용자가 엉뚱한 입력을 한다면, 정확한 입력을 해달라는 안내문이 출력된다.   
![미니게임기 실행12 잘못된 이름](https://user-images.githubusercontent.com/101881124/212483189-e1dd73c2-2f72-44b9-b45c-4ca700ae8763.jpg)
![미니게임기 실행13 가위바위보 잘못입력](https://user-images.githubusercontent.com/101881124/212483193-2b814ffa-24e9-4a68-85f0-8b225367f621.jpg)
![미니게임기 실행14 참참참 잘못입력](https://user-images.githubusercontent.com/101881124/212483195-96d9a2bb-caf0-4001-bd94-ebeeab759e12.jpg)

# 4. 고찰
- 가위바위보나 참참참은 시간 요소가 상관없기 때문에 비교적 만들기 수월했다. 반면에 우유 빨리 마시기 게임은 시간 측정과 마신 우유 잔 수를 표현하는 과정에서 시행착오를 겪었다. 실행문이 작동한 시간을 측정하고, 사용자에게 입력받은 문자열에서 'milk'의 갯수를 세는 방식을 사용하였다.   
- 마셔야 하는 우유 잔 수의 random 범위와 제한 시간을 설정할 때 여러 번의 테스트를 진행했다. 게임에서 이기거나 질 확률이 적정한 비율이 되도록, 많이 고민해야 하는 부분인 것 같았다.   
