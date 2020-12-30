# KOSPI200 MD&A 가독성과 수익률에 관한 분석
## ABSTRACT
- Dart 기업 공시에 매년 1번씩 공시되는, 기업이 제출한 사업보고서의 재무제표 등 정형 데이터를 이용하는 것이 아닌 비정형 데이터인 텍스트를 이용하여 해당 기업의 수익률을 예측해본다. 문장 내 단어의 개수, 복잡한 단어의 비중, 문서의 길이를 이용하여 사업보고서의 핵심 파트인 MD&A(이사의 경영진단 및 분석의견)의 가독성을 측정하고, KOSPI200 기업의 가독성의 추이에 관해 살펴보고, 그 가독성과 수익률 간의 상관관계를 살펴보았다. 그 결과, 가독성이 좋은(읽기 쉬운) 사업보고서를 작성한 기업의 수익률은 가독성이 나쁜(읽기 어려운) 사업보고서를 작성한 기업의 수익률보다 높았을 뿐 아니라, 미래의 수익률도 높았다.

## 참고 논문
- Schroeder_Gibson(AH 1990) Readbility of Managements Discussion and Analysis
- Li(2008 JAE) Annual report readability, current earnings, and earnings persistence

# 코드 순서
1. Dart_Crawling_final.ipynb
2. Data_setting.ipynb
3. Preprocessing.ipynb
4. Perfect_crp(exactly 10 years MD&A).ipynb
5. Get_KOSPI200_Return.ipynb
6. 

## Dart_Crawling_final.ipynb
- Dart 기업 공시에는 기업별 코드를 이용하여 사업보고서를 추출할 수 있는 자체적인 API를 지원한다. 해당 코드는 이 API를 활용하여 KOSPI200 기업별 2010년부터 2019년까지의 모든 사업보고서를 추출하여 '이사의 경영진단 및 분석의견'(MD&A) 파트만 크롤링해오는 과정이다. 이 과정에서 재무제표 등과 같은 정형 데이터는 제외하고 텍스트만 크롤링해왔다.
- 주의사항 : Dart API를 사용한다고 해도, 짧은 시간(초 단위)동안 너무 많은 데이터를 추출하려고 하면 자동으로 IP가 차단된다. 이에 대한 해결책은 코드 내에 명시되어 있다. ("현행 DART 시스템 하에서는 10초 미만의 간격으로 빈번하게 내려 받기 요청을 보낼 경우, 이를 DART 서버에 대한 공격으로 간주하여 해당 IP 주소를 차단하도록 되어 있다(김형준 등 2015).")

## Data_setting.ipynb
- 

## Preprocessing.ipynb
- 전처리 코드

## Perfect_crp(exactly 10 years MD&A).ipynb
- 가독성 분석 프로젝트를 좀 더 수월하게 진행하기 위해, 총 10년(2010~2019년)의 기간동안 KOSPI200에 모두 포함됐고, 정확히 10년치 사업보고서가 존재하는 기업을 구하는 과정이다. 이러한 기업들을 편의상 perfect_crp라고 칭한다.

## Get_KOSPI200_Return.ipynb
- 생존편향을 제거한(전체 10년의 기간동안 1번이라도 KOSPI200에 편입된 적 있었던 기업들(lv2_companies)은 모두 포함한) KOSPI200 기업들의 '종가'와 '수익률'을 추출하여 저장하는 작업이다.
- 사전에 정제해놓은 'new_df_bfconv.csv'(행 : symbol name, 열 : date(20100101부터 20191231)) 에는 총 10년 간 KOSPI200을 구성하고 있던 모든 종목이름과 기업코드 정보가 들어있다. 여기서 모든 종목이름과 기업코드를 딕셔너리 형태로 만들어 사용했고, lv2_companies의 정보를 담은 'date_df.csv'도 활용하였다.

## Readability_measurements.ipynb
- Fog index 계산 코드
