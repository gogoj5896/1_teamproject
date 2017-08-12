
# <강남 아파트 가격과 스타벅스 및 맥도날드의 관계 분석> 
<br />

## 1. 분석동기 
### 1) 스타벅스와 맥도날드가 근처에 있으면 집값이 오른다? 
![starmc](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/starmc.jpg?raw=true)

“2015년 3월 CNN머니는  미국 부동산 업체인 질로 (https://www.zillow.com/ )의 조사 결과를 인용해 1997년에서 2013년 사이 스타벅스와 가까이 있는 주택 가격이 평균 96% 상승해 미국 전체 평균인 65%를 앞질렀다고” 보도했습니다. 

 과연 한국에서도 비슷한 현상이 일어났을까 의문이 들어 조사를 시작했습니다.  스타벅스나 맥도날드가 집 근처에 있으면 내 집 가격이 상승할 것인가? 
 
http://www.koreadaily.com/news/read.asp?art_id=3217847

### 2) 강남을 선정하게 된 이유는?
- 강남은 starbucks 및 mcdonalds등이 다른 구보다 많아서,  아파트 값과 상관관계를 찾아보는 것에 있어서 좋은 data일 것이라고 생각 함 

### 3) 분석의 가설(귀무가설)
 -  즉 우리는 "스타벅스 및 맥도날드가 아파트 근처에 있을 수록 땅값이 비싸다."   **양의 관계**가 있을 것이라고 가정하고 이를 검토하는 것이 아래의 과정이다.
<br />
<br />

##  2. 데이터 변수 설명 

|  | 출처 |  데이터 변수  | 데이터 개수 |
|-----------------------|----------------------------------------------|----------------------|-------------|
| 아파트 실거래가 | 국토 교통부(http://rt.molit.go.kr/) | 전용면적, 가격, 주소 | 6000개 |
| 편의시설(스타벅스 등) | 각 홈페이지(http://www.istarbucks.co.kr/ 등) | 주소 | 100개 |

<br />
<br />


## 3. Data 처리 방법 

### 3-(1) 아파트 데이터 처리 
* 강남구 데이터 정리
* Google map API 를 APT주소 이용한 GPS 좌표변환

### 3-(2) 크롤링을 이용한 스타벅스 & 맥도날드 gps 좌표
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/crawl.png?raw=true)
<br />
<br />



## 4. 시각화 

### (1) 지도형태로 살펴보기 - maplotlib 이용하기
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/fish.png?raw=true)
- 위와 같이 좌표평면에 그리게 되면 도로 및 지형물 등을 고려하지 못하므로, 파이썬 다른 패키지를 이용해서 시각화 시도!
<br />

### (2) 지도형태로 살펴보기 - folium package 이용하기
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gangnam_2.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gangnam_3.png?raw=true)
- 2차원 좌표평면에 시각화 하면서 스타벅스의 분포 및 맥도날드의 분포의 패턴은 파악 할 수 있었다.
- 하지만 이를 통해서 아파트 가격과의 관계를  수치적으로 파악이 불가하므로, 이하에서는 joint plot등으로 관계를 살펴보도록 하겠다.
<br />

## (3) 데이터 분포 및 관계의 시각화
- 아파트 기준으로 가장 가까운 맥도날드 및 스타벅스의 거리를 구하고, 그 거리와 아파트 값의 관계를 살펴본다.
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gps_form.png?raw=true)
<br />

(3)-1. 강남의 경우
- jointplot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gps_form.png?raw=true
