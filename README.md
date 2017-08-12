
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
- htmlfile -> gangnam_map.html
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gangnam_3.png?raw=true)
- htmlfile -> gangnam_map1.html

- 2차원 좌표평면에 시각화 하면서 스타벅스의 분포 및 맥도날드의 분포의 패턴은 파악 할 수 있었다.
- 하지만 이를 통해서 아파트 가격과의 관계를 수치적으로 파악이 불가하므로, 이하에서는 joint plot등으로 관계를 살펴보도록 하겠다.
<br />

## (3) 데이터 분포 및 관계의 시각화
- 아파트 기준으로 가장 가까운 맥도날드 및 스타벅스의 거리를 구하고, 그 거리와 아파트 값의 관계를 살펴본다.
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/gps_form.png?raw=true)
<br />

### (3)-1 강남구의 경우
- distplot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/distplot.png?raw=true)
- joint plot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/7.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/8.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/9.png?raw=true)
- regplot!
[pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/10.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/11.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/12.png?raw=true)
#### regplot으로 볼 경우에는 우리가 예상한 집 값과 맥도날드 등과의 음의 관계와 반대되는 양의 관계가 나온다. 
#### 하지만 위에서 살펴본 jointplot의 p값이 0.1이상이므로 이를 받아들일 수 없다.
<br />
#### 그렇다면 강남과 지리적으로 가까운 다른구의 경우에는 집 값과 맥도날드등의 관계를 추가적으로 살펴보기로 하였다.
#### 이하에서는 송파구의 경우에 대해서 알아보도록 하겠다.
<br />

### (3)-2 송파구의 경우(추가 분석)
- distplot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/distplot_2.png?raw=true)
- joint plot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/1.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/2.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/3.png?raw=true)
- regplot
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/4.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/5.png?raw=true)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/6.png?raw=true)
#### 스타벅스와의 거리, 맥도날드와의 거리 , 이 둘의 합 모두 음의관계가 나오며 p-value값이 0.01미만으로 나와서 상관관계가 있다고 볼 수 있다.
#### 즉 우리가 가정한 스타벅스 및 맥도날드가 주변에 있을 수록 땅 값이 비싸다와 일치하는 지역이다.
<br />
<br />

# 5.그렇다면 강남의 경우에는 왜 가정이 성립하지 않는 것일까?
### * 기타 정보 등으로 원인 추측(추후 분석과제)
![pic](https://github.com/gogoj5896/1_teamproject/blob/master/image%20file/after.png?raw=true)
## 1) 주거지역 및 상업시설의 혼재
수 많은 상업시설(은행, 회사 등)이 모여있으며 이러한 유동인구를 target으로 스타벅스 및 맥도날드 등이 위치해 있다.
하지만 우리가 고려한 것은 아파트의 평당 가격이어서 거주지역에 대해서만 고려한 것이라 유동인구 등에 대해 고려하지 못했다.
## 2) 땅 값에 미치는 다양한 영향
2-1) 개포동, 압구정동 재건축
2-2) 한강조망권과 숲세권
2-3)대치동 학군

#### 등 다양한 요인이 아파트 가격을 결정하고 있어서 맥도날드 등과의 관계가 뚜렷하지 못했다.
<br />
<br />

# 6. 추후과제(further study)
###  1) 서울 전체에 대해서 분석해보기
- 서울 전체 데이터로 상관관계 있는지 살펴보고, 개별 구마다 검토하기
###  2) 다른 편의 시설의 유무도 고려하기 
 - 스타벅스, 맥도날드 및 다른 편의시설 유무도 고려하기
 ### 3) 아파트 뿐만 아니라 다른 주거형태(원룸, 빌딩) 및 빌딩 등 고려하기
 ### 4) 강남의 경우 땅 값에 미치는 요인에 대해서 검토해보기
