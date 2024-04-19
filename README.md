# DE-1st-jeju
## Analysis of Changes in Tourism Trends in Jeju Island (제주도 관광 트렌드 변화 분석)

## 개요
저희 제주팀은 국내 여행 중에서도 제주도의 관광 트렌드가 2009년부터 2023년까지 어떻게 변화하였는지 분석하였습니다.

## 서론
### 분석 배경
제주도의 관광은 활성화되어 있지만, 지역마다 관광객 방문의 편차가 심하며 고착화되어 있는 경향이 있습니다. 이번 분석을 통해 내국인의 관광 성향의 변화를 파악해보려 하였습니다.

### 분석 목적
이 분석을 통해, 두 공공데이터를 통해 분석하여 제주 관광 사업의 발전 뿐만 아니라 트렌드에 민감한 자영업자에게 운영 방향성에 도움을 주거나, 여행사에게 새 여행상품을 제작하는 데에 도움을 주거나, 관광객에게는 제주 관광 계획에 도움을 주는 등 다양한 영역에 사용 가능한 인사이트를 제공할 수 있을 것으로 예상합니다.

## 본론
### 개발 환경
Python : Jupyter-Notebook / conda 24.1.2 / Python 3.9.19

IDE : VSCode

Modules : sqlalchemy / urllib / selenium / time / random / re / pandas / pickle / requests / BeautifulSoup

MySQL : HeidiSQL

Visualization Tools : Tableau

### 활용한 데이터 설명 및 전처리 과정 설명
첫 번째로, 공공데이터 포털에서 제주도내 관광객 소비 패턴을 알 수 있는 카드데이터와 제주도의 상권 변화를 알 수 있는 업장 개,폐업 데이터를 수집하였습니다. 먼저, 과거 카드 데이터는 날짜, 관광 업종, 제주도 주소, 내국인/제주도민 카드이용자수, 카드이용금액 등으로 구성되어 있습니다. 제주도민을 제외하고 내국인 관광객을 중점으로 전처리를 하였으며, 관광업종별로 금액대가 다른 변수를 제거하기 위해 카드이용금액이 아닌 카드이용자수로 데이터 분석을 진행하였습니다.

두 번째로, 제주 업장 데이터는 1960년대부터 현재까지의 업종별, 인허가 일자, 폐업 일자, 주소 등으로 구성되어있습니다. 기간을 2009년-2014년과 2018년-2023년으로 나누어 각각 past와 lately로 그룹화 하여, 폐업 일자와 개업 인허가 일자를 활용하여 누적 점포수를 계산하였습니다.

그 외에도 2018년 부터 2023년 까지의 내국인 관광객들의 여행 트렌드를 파악하기 위해서 네이버 지도에서 제주도 식당, 음식점, 카페 정보를 selenium 모듈을 이용하여 크롤링을 진행하였습니다. 또한, 구글 트렌드에서 제주도 여행, 애월, 한달살기 등의 키워드를 입력하여 각 키워드 간의 검색량을 상대적으로 비교하고 추이도 볼 수 있도록 시각화를 진행하였습니다.


## 결론
### 마무리
시각화한 데이터를 통하여 과거(09 ~ 14년) → 최근(18 ~ 23년) 제주 관광객의 소비 트랜드는 유의미하게 변화했으며, 대체적으로 증가율 또한 점점 높아지고 있는 모습을 확인할 수 있습니다. 관광 소비 트랜드의 변화가 큰 제주도 지역을 추출하였으며, 제주도 지역간 관광객들의 지출 경향을 파악할 수 있었습니다. 

### API & Data used
- [도로명 주소를 지번 주소로 변경](https://www.juso.go.kr/openIndexPage.do)
- [네이버 지도](https://map.naver.com/p/search/%EC%A0%9C%EC%A3%BC%EB%8F%84/address/14090357.3876139,3952164.1450325,%EC%A0%9C%EC%A3%BC%ED%8A%B9%EB%B3%84%EC%9E%90%EC%B9%98%EB%8F%84,jibun?c=7.00,0,0,0,dh&isCorrectAnswer=true)
- [구글 트렌드](https://trends.google.co.kr/trends/explore?date=2009-01-01%202023-12-31&geo=KR&q=%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EC%97%AC%ED%96%89,%EC%95%A0%EC%9B%94,%EC%A1%B0%EC%B2%9C,%ED%95%B4%EC%99%B8%EC%97%AC%ED%96%89,%ED%95%9C%EB%8B%AC%EC%82%B4%EA%B8%B0&hl=ko)
- [제주특별자치도 관광객 소비패턴 변화 분석 데이터(카드 소비)](https://www.data.go.kr/data/15046091/fileData.do)
- [제주특별자치도 관광객 소비패턴 변화 분석 데이터(업종)](https://www.data.go.kr/data/15046087/fileData.do)
- [제주특별자치도 음식점 목록](https://www.jejudatahub.net/data/view/data/780)
