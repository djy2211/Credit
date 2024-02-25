# Credit

데이콘 - 고객 대출등급 분류 해커톤
https://dacon.io/competitions/official/236214/overview/description

위 데이터를 기반으로 정형 데이터 분석

train 데이터를 분석해보고, 간단한 모델을 사용하여 submission을 제출


=========================================

주어진 데이터의 컬럼은 아래와 같음

 0   ID            96294 non-null  object 
 
 1   대출금액          96294 non-null  int64  
 
 2   대출기간          96294 non-null  object 
 
 3   근로기간          96294 non-null  object 
 
 4   주택소유상태        96294 non-null  object 
 
 5   연간소득          96294 non-null  int64  
 
 6   부채_대비_소득_비율   96294 non-null  float64
 
 7   총계좌수          96294 non-null  int64  
 
 8   대출목적          96294 non-null  object 
 
 9   최근_2년간_연체_횟수  96294 non-null  int64  
 
 10  총상환원금         96294 non-null  int64  
 
 11  총상환이자         96294 non-null  float64
 
 12  총연체금액         96294 non-null  float64
 
 13  연체계좌수         96294 non-null  float64
 
 14  대출등급          96294 non-null  object 

========================================================

========

 주택소유상태 컬럼의 값들을 확인한 결과, 'RENT', 'MORTGAGE', 'OWN' 3 가지 값이 존재
 
 ### one-hot 적용

========

 대출기간은 36개월 or 60개월
 
 ### 36, 60 으로 수정

========

 근로기간은 1년 단위로 값이 측정이 되었고, 1년 보다 낮으면 '< 1 year' 10년 이상이면 '10+years' 로 표시 되었음
 
 ### 단위 년도별로 라벨링 (0 ~ 10)

========
 

대출목적 one-hot 적용


========


연간 소득은 drop 하였음 / 부채 대비 소득 비율과 대출 금액에 대한 컬럼 값만 있어도 될 것이라 판단


========


위 데이터를 기반으로 DecisionTreeClassifier 적용

Train 데이터 기반 / 정확도 0.83


=================================

학습된 모델을 기반으로 test 데이터 적용 시도

=

Train '대출 목적' 컬럼에 없던 '결혼' 이라는 값이 test에는 존재

>>> one-hot으로 모든 대출 목적 값이 0인 경우로 잡으면 되기에 문제 없이 predict 진행


====

submission 생성 후 제출하였습니다.
