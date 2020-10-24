# NLP
Dart Crawling

# 코드 순서
1. 
2. 
3. 

## Perfect_crp(exactly 10 years MD&A).ipynb
- 가독성 분석 프로젝트를 좀 더 수월하게 진행하기 위해, 총 10년(2010~2019년)의 기간동안 KOSPI200에 모두 포함됐고, 정확히 10년치 사업보고서가 존재하는 기업을 구하는 과정이다. 이러한 기업들을 편의상 perfect_crp라고 칭한다.

## Get_KOSPI200_Return.ipynb
- 생존편향을 제거한(전체 10년의 기간동안 1번이라도 KOSPI200에 편입된 적 있었던 기업들(lv2_companies)은 모두 포함한) KOSPI200 기업들의 '종가'와 '수익률'을 추출하여 저장하는 작업이다.
- 사전에 정제해놓은 'new_df_bfconv.csv'(행 : symbol name, 열 : date(20100101부터 20191231)) 에는 총 10년 간 KOSPI200을 구성하고 있던 모든 종목이름과 기업코드 정보가 들어있다. 여기서 모든 종목이름과 기업코드를 딕셔너리 형태로 만들어 사용했고, lv2_companies의 정보를 담은 'date_df.csv'도 활용하였다.
