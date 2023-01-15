---
layout: single
title: "[python] 세대 시간에 따른 박테리아 증식"
---

# 1. 제작 동기   
박테리아(세균)는 이분법을 통해 exponential phase에서 기하급수적으로 증가한다. 수학적으로도 의미가 있는 생물학적 현상을 프로그래밍을 통해 실시간으로 확인할 수 있으면 재밌겠다고 생각했다. 세균의 수가 2배가 되는데 걸리는 시간을 세대 시간(generation time)이라고 하며, 세균의 종류에 따라 세대 시간은 모두 다르다. 사용자는 자신이 원하는 박테리아의 종류에 따라 세대 시간을 입력하고, 증식 주기마다 정확한 숫자와 함께 시각적으로 증식한 박테리아의 개수를 확인할 수 있다.    

# 2. 작성한 코드
```python
# 박테리아의 증식 세대 시간을 입력받고, 세대 시간 한 cycle이 돌 때마다 시간과 박테리아의 수를 출력한다.

import schedule
import time

def static_vars(**kwargs):
    def decorate(func):
        for k in kwargs:
            setattr(func, k, kwargs[k])
        return func
    return decorate

generation_time = int(input("박테리아의 세대 시간을 초 단위로 입력하시오: "))

@static_vars(num_of_bacteria=1)
@static_vars(count=1)
def proliferation():
    proliferation.num_of_bacteria *= 2
    print("="*40)
    print(f"{generation_time*proliferation.count}초 경과했을 때 박테리아 수는 {proliferation.num_of_bacteria}입니다.") 
    print("*"*proliferation.num_of_bacteria, "\n")  # *은 박테리아 1개를 나타낸다.
    proliferation.count += 1

job = schedule.every(generation_time).seconds.do(proliferation)
stop_count = 0
while True:
    schedule.run_pending()
    time.sleep(1)
    stop_count += 1
    if stop_count > 50:
        schedule.cancel_job(job)
```

# 3. 실행 결과
- schedule() 모듈과 time() 모듈을 사용하여, 세대 시간이 지날 때마다 프로그램이 자동으로 경과된 시간과 박테리아의 수, 그리고 박테리아 수만큼 *을 출력한다. 성공적으로 실행되었다.   
![bacteria_proliferation 실행1](https://user-images.githubusercontent.com/101881124/212479733-391e2007-485a-4aed-ab7f-9149a4526698.jpg)
![bacteria_proliferation 실행2](https://user-images.githubusercontent.com/101881124/212479738-467fd768-6f02-4c5a-80b6-a0cabbd09756.jpg)
![bacteria_proliferation 실행3](https://user-images.githubusercontent.com/101881124/212479747-3c584e5f-6969-49ad-9957-57ea76ecfeac.jpg)
![bacteria_proliferation 실행4](https://user-images.githubusercontent.com/101881124/212479754-5f370d18-6468-4901-ae0e-ec1abafb0037.jpg)

# 4. 고찰
- 초기 박테리아 수를 'num_of_bacteria = 1'로 지정하려고 했으나, 지역 변수여도 전역 변수여도 함수 안에서 값을 변화시킨 후에 계속 초기화되는 문제가 발생했다. static_vars() 함수를 활용하여 변수를 선언하였다. 그 결과, 다른 함수 내에서 변화된 변수의 값이 초기화되지 않고 저장될 수 있었다.   
- 아래는 처음에 문제를 겪었던 코드와 실행 결과이다.   
![bacteria_proliferation 문제상황2](https://user-images.githubusercontent.com/101881124/212479787-a8353caa-cb38-4477-86e6-7dd09fc4074e.jpg)
![bacteria_proliferation 문제상황1](https://user-images.githubusercontent.com/101881124/212479791-f1f7c53c-885d-402f-8cc3-958471259667.jpg)
