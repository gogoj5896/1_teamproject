
# <강남 아파트 가격과 스타벅스 및 맥도날드의 관계 분석> 

## 1. 분석동기 
### 1) 스타벅스와 맥도날드가 근처에 있으면 집값이 오른다? 

“2015년 3월 CNN머니는  미국 부동산 업체인 질로 (https://www.zillow.com/ )의 조사 결과를 인용해 1997년에서 2013년 사이 스타벅스와 가까이 있는 주택 가격이 평균 96% 상승해 미국 전체 평균인 65%를 앞질렀다고” 보도했습니다. 

 과연 한국에서도 비슷한 현상이 일어났을까 의문이 들어 조사를 시작했습니다.  스타벅스나 맥도날드가 집 근처에 있으면 내 집 가격이 상승할 것인가? 
 
http://www.koreadaily.com/news/read.asp?art_id=3217847


### 2) 강남을 선정하게 된 이유는?
- 강남은 starbucks 및 mcdonalds등이 다른 구보다 많아서,  아파트 값과 상관관계를 찾아보는 것에 있어서 좋은 data일 것이라고 생각 함 

### 3) 분석의 가설(귀무가설)
 -  즉 우리는 "스타벅스 및 맥도날드가 아파트 근처에 있을 수록 땅값이 비싸다."   **양의 관계**가 있을 것이라고 가정하고 이를 검토하는 것이 아래의 과정이다.

##  2. 데이터 변수 설명 

|  | 출처 |  데이터 변수  | 데이터 개수 |
|-----------------------|----------------------------------------------|----------------------|-------------|
| 아파트 실거래가 | 국토 교통부(http://rt.molit.go.kr/) | 전용면적, 가격, 주소 | 6000개 |
| 편의시설(스타벅스 등) | 각 홈페이지(http://www.istarbucks.co.kr/ 등) | 주소 | 100개 |


## 3. Data 처리 방법 

### 3-(1) 아파트 데이터 처리 
* 강남구 데이터 정리
* Google map API 를 APT주소 이용한 GPS 좌표변환

### 3-(2) 크롤링을 이용한 스타벅스 & 맥도날드 gps 좌표



## 4. 시각화 

### (1) 지도형태로 살펴보기 - maplotlib 이용하기

### 아파트 위치와 평당가격을 좌표평면에 그리는 함수
###  아파트, 스타벅스, 맥도날드 위치를 지도에 Mapping하기


### (2) 지도형태로 살펴보기 - folium package 이용하기


- 패키지를 이용해서 강남지역 지도로 띄우기
- map1이 실행을 안시키면 사진이 안뜨는 경우가 있어서 그 밑에 캡쳐사진을 첨부

map1 = folium.Map(location=[37.505,127.06],zoom_start=12,tiles="Stamen Toner")
map1

![gangnam](https://github.com/gogoj5896/1_teamproject/blob/master/gangnam_1.png?raw=true)<br />

- 평당가격을 색깔의 진함으로 표현한다.

data = open('11.txt','r+')
data_1 = data.read()
Bs_read = BeautifulSoup(data_1, "html.parser")
Parsed_data = Bs_read.findAll(class_="quickResultLstCon")

gn_lat_list = []
gn_long_list = []
gn_data_list = []

for i in range(len(Parsed_data)):
    for j in range(len(Parsed_data)):
        if i == j:
            gn_lat_list.append(Parsed_data[i]["data-lat"])
            gn_long_list.append(Parsed_data[j]["data-long"])
            gn_data_list.append(Parsed_data[i]["data-name"])
        else:
            pass

df_gangnam_star = pd.DataFrame({
        'name': gn_data_list,
        'lat': gn_lat_list,
        'long': gn_long_list
    },columns=['name', 'lat', 'long']
)
df_gangnam_star.to_csv("gangnam_star_gps", sep='\t', encoding='utf-8')
df_gangnam_star.head(10)

