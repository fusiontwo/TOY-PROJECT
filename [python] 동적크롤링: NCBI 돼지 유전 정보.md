---
layout: single
title: "[python] 동적크롤링: NCBI 돼지 유전 정보"
---

# 1. 제작 동기   
NCBI(National Center for Biotechnology Information)에는 방대한 유전학적 정보가 존재한다. 사이트에 흩어져 있는 정보를 빠르고 깔끔하게 합쳐서 엑셀 파일로 만들고 싶었다. Selenium과 BeautifulSoup을 활용하여 정적 크롤링을 진행하였다. 크롤링에 익숙해지면 데이터를 분석하기 전에 모으는 과정이 효율적으로 변화할 것이다.   

# 2. 작성한 코드 및 실행 결과
- selenium을 통해 NCBI에서 원하는 정보가 있는 곳까지의 클릭 및 검색어 입력 경로를 자동화하였다.   
- BeaultifulSoup을 통해 원하는 정보를 파이썬 작업 환경으로 가져왔다.   
- select()를 이용하여 원하는 정보만 추출하고, replace()를 이용하여 불필요한 문자열을 제거했다.   
- 데이터프레임 df1에는 항목 정보를, df2에는 항목에 대한 자세한 정보를 저장했다.   
- df2의 경우, raw data의 패턴이 달라서 추출이 어려운 정보가 7개 존재하였다. 예외적으로 직접 확인하고 수정했다.   
- df1과 df2를 concat()으로 합쳐 final_df에 저장하고, .to_csv()를 통해 엑셀 파일로 저장했다.   
![NCBI크롤링1](https://user-images.githubusercontent.com/101881124/212549001-e2a77ddb-7194-479f-9d65-f21dcafdd124.jpg)
![NCBI크롤링2](https://user-images.githubusercontent.com/101881124/212549005-39aa2a23-1d5b-44d1-9c71-673a5a9c8e15.jpg)
![NCBI크롤링3](https://user-images.githubusercontent.com/101881124/212549009-3b04a23c-55df-472f-a277-defcb508c2c6.jpg)
![NCBI크롤링4](https://user-images.githubusercontent.com/101881124/212549010-86799001-37c4-4511-89f0-6ecc8d598b9a.jpg)
![NCBI크롤링5](https://user-images.githubusercontent.com/101881124/212549013-40d56b7b-9ae9-4ac1-9a46-3d1b7910775b.jpg)
![NCBI크롤링6](https://user-images.githubusercontent.com/101881124/212549015-ed071b15-01d9-4e67-8ad5-159c372c1915.jpg)
![NCBI크롤링7](https://user-images.githubusercontent.com/101881124/212549016-c916071f-d824-432c-9901-4e76a687cd56.jpg)

- 데이터의 누락 없이 엑셀 파일로 성공적으로 저장되었다.
![NCBI크롤링8](https://user-images.githubusercontent.com/101881124/212549018-030a6881-f12e-48b6-a5c1-0616f08373c9.jpg)
![NCBI크롤링9](https://user-images.githubusercontent.com/101881124/212549022-f978de35-6a5e-4d4a-936f-c8871154d6f5.jpg)
![NCBI크롤링10](https://user-images.githubusercontent.com/101881124/212551031-05cef634-88c9-48a5-a0c2-c3ef084e08e7.jpg)  

# 3. 고찰
성공적으로 정적 크롤링을 통해 NCBI의 돼지의 유전 정보에 대한 데이터를 가져왔다. 보완할 부분은 패턴이 많이 달라서, 직접 수정했던 데이터 7개였다. 다양한 코드를 시도해보았으나 예외적인 패턴을 처리할 방법은 찾기 어려웠다. 앞으로 가장 간단한 코드로 원하는 데이터만을 추출할 수 있도록 다양한 사이트나 정보에 접근하여 크롤링을 연습해야 할 것 같다.   
