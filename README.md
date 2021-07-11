# <Analysis_Of_Scale_Defective_Rate_Factor>  
[POSCO_AC_Project] 압연 공정에서 발생하는  SCALE 불량에 대한  주요 영향인자 분석

---
## Data
- 데이터 csv 파일은 공유하지 않음.  
- 변수 설명  
![SCALE불량_변수정의성 ](https://user-images.githubusercontent.com/80561963/125194131-f5ac3500-e28a-11eb-9a6f-2d27ebf2f190.JPG)
- 'FUR_SZ_TEMP'와 'FUR_EXTEMP' 데이터가 같기 때문에 하나로 통일('FUR_EXTEMP' 삭제)
- 파생변수 밀도('PT_DSY' = 'PT_WGT' / ('PT_THK'+'PT_WDTH'+'PT_LTH')) 생성
- STEEL_KIND(강종) 소분류 되어있는 것을 C(일반강)와 T(TMCP강) 대분류로 변경
- ROLLING_TEMP_T5의 이상치 6개 제거
---
## EDA
- 2-Sample T 검정 결과, 제품의 밀도(PT_DSY)가 증가할수록 SCALE 불량이 증가할 것이다.  
![규격](https://user-images.githubusercontent.com/80561963/125194852-0ca05680-e28e-11eb-98f6-eb0c209f321c.JPG)  
- Welch's T 검정 결과, 균열대 온도(FUR_SZ_TEMP)가 증가할수록 Scale 불량이 증가할 것이다.  
![온도](https://user-images.githubusercontent.com/80561963/125194857-16c25500-e28e-11eb-8b71-b3b23900b4ea.JPG)  
- 카이제곱 검정 결과, 강종(STEEL_KIND)별 SCALE 불량 수의 차이가 있다고 말할 수 있다.  
![강종](https://user-images.githubusercontent.com/80561963/125194867-20e45380-e28e-11eb-9c20-b250c2e4f80a.JPG)  
---
## Modeling
- 모델선정  
![모델선정](https://user-images.githubusercontent.com/80561963/125194947-67d24900-e28e-11eb-8f38-c3df759a6b06.JPG)
> GradientBoosting이 전체적으로 성능이 좋음 :arrow_right: 최종 모델로 GradientBoosting 선정
- 변수중요도  
![변수중요도](https://user-images.githubusercontent.com/80561963/125194962-76206500-e28e-11eb-98e6-867c3bd0d747.JPG)
> SCALE 불량과 관련하여 ROLLING_TEMP_T5, HSB, FUR_SZ_TEMP, ROLLING_DESCALING 등 순으로 영향이 크다고 해석할 수 있음
---
## Report
[Analysis_Of_Scale_Defective_Rate_Factor_Report.pptx](https://github.com/colin9597/Analysis_Of_Credit_Card_Company_Data/files/6796894/Analysis_Of_Scale_Defective_Rate_Factor_Report.pptx)
