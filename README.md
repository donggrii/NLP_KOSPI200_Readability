# KOSPI200 MD&A 가독성과 수익률에 관한 분석
## ABSTRACT
- 2010년 ~ 2019년 KOSPI200 기업 사업보고서의 MD&A(이사의 경영진단 및 분석의견) 파트의 가독성(Readability)과 실제 수익률(Return) 간의 관계를 분석한 프로젝트
- <b>결과 : 가독성이 좋은(읽기 쉬운) 사업보고서를 작성한 기업의 수익률은 가독성이 나쁜(읽기 어려운) 사업보고서를 작성한 기업의 수익률보다 높았고, 미래 수익률도 높았음</b>
- 문장 내 단어의 개수, 복잡한 단어의 비중, 문서의 길이 등을 이용하여 사업보고서 MD&A의 Readability 측정
- 기존의 많은 연구에서 다뤄졌던 재무제표와 같은 정형 데이터를 이용하는 게 아닌 비정형 데이터인 텍스트를 활용하여 KOSPI200 수익률을 예측했다는 것이 차별화된 점

## 참고 논문(paper)
- Content_Schroeder_Gibson(AH 1990)Readbility of Managements Discussion and Analysis
- Readability_Li(2008 JAE)Annual report readability, current earnings, and earnings persistence
- 우리말 사업보고서 가독성 연구의 가능성에 대한 탐색적 연구
- 홍정하 등(2011) - 텍스트 수준과 가독성 한국어 학습 교재를 이용한 검증과 응용

# 코드 순서
1. Dart_Crawling_final.ipynb
2. Data_setting.ipynb
3. Preprocessing.ipynb
4. Perfect_crp(exactly 10 years MD&A).ipynb
5. Get_KOSPI200_Return.ipynb

## Dart_Crawling_final.ipynb
- 기업별 코드를 이용하여 사업보고서를 추출할 수 있는 Dart API를 활용하여 2010년 ~ 2019년 KOSPI200 기업별 사업보고서를 추출하여 '이사의 경영진단 및 분석의견'(MD&A) 파트만 크롤링하는 코드
- 재무제표 등과 같은 정형 데이터는 제외하고 텍스트만 크롤링함
- 주의사항 : Dart API를 사용한다고 해도, 짧은 시간동안 너무 많은 데이터를 추출하려고 하면 자동으로 IP가 차단됨

`"현행 DART 시스템 하에서는 10초 미만의 간격으로 빈번하게 내려 받기 요청을 보낼 경우, 이를 DART 서버에 대한 공격으로 간주하여 해당 IP 주소를 차단하도록 되어 있다(김형준 등 2015)."`

## Data_setting.ipynb

## Preprocessing.ipynb
- 전처리 코드

## Perfect_crp(exactly 10 years MD&A).ipynb
- 가독성 분석 프로젝트를 좀 더 수월하게 진행하기 위해, 총 10년(2010~2019년)의 기간동안 KOSPI200에 모두 포함됐고, 정확히 10년치 사업보고서가 존재하는 기업을 구하는 코드
- 이러한 기업들을 편의상 `perfect_crp`라고 정함

## Get_KOSPI200_Return.ipynb
- 생존편향을 제거한(전체 10년의 기간동안 1번이라도 KOSPI200에 편입된 적 있었던 기업들(lv2_companies)은 모두 포함한) KOSPI200 기업들의 `종가`와 `수익률`을 추출하여 저장하는 코드
- 사전에 정제해놓은 'new_df_bfconv.csv'(행 : symbol name, 열 : date(20100101부터 20191231)) 에는 총 10년 간 KOSPI200을 구성하고 있던 모든 종목이름과 기업코드 정보가 들어있음
- 여기서 모든 종목이름과 기업코드를 Dictionary 형태로 만들어 사용했고, lv2_companies의 정보를 담은 'date_df.csv'도 활용함
- 사전에 정제해놓은 'new_df_bfconv.csv'(행 : symbol name, 열 : date(20100101부터 20191231)) 에는 총 10년 간 KOSPI200을 구성하고 있던 모든 종목이름과 기업코드 정보가 들어있음여기서 모든 종목이름과 기업코드를 딕셔너리 형태로 만들어 사용했고, lv2_companies의 정보를 담은 'date_df.csv'도 활용하였다.

## Readability_measurements.ipynb
- Fog index 계산 코드
