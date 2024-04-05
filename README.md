개별 모델링 파일에 있는 df3.csv 는 전처리.ipynb 에 나온 방식대로 전처리를 진행하여 얻은 통일 전처리 데이터프레임입니다.

![df3.csv]([https://github.com/jparkgit/Dacon-Credit-Card-Deliquency-Level-Classification/blob/main/df3.csv]) 자체도 repository에서 찾을 수 있습니다.

고용된 여부에 따라 sub population으로 나눠 별개 모델링을 구현하는 방식에 사용된 [XGB_LGBM_RF_Voting_지현]([https://github.com/jparkgit/Dacon-Credit-Card-Deliquency-Level-Classification/blob/main/XGB_LGBM_RF_Voting_지현.ipynb])의 [df_emp.csv]([https://github.com/jparkgit/Dacon-Credit-Card-Deliquency-Level-Classification/blob/main/df_emp.csv]), [df_unemp.csv]([https://github.com/jparkgit/Dacon-Credit-Card-Deliquency-Level-Classification/blob/main/df_unemp.csv]) 또한 업로드되어 있습니다.

전처리 내용:
- index: 삭제
- gender, car, reality: LabelEncoder()
- child_num: 삭제
- income_total: 로그 변환한 log_income_total로 대체
- income_type: pd.get_dummies
- edu_type: ordinal 특성 고려하여 mapping된 edu_type_encoded로 대체
- family_type: pd.get_dummies
- house_type: pd.get_dummies
- DAYS_BIRTH: abs() 후 //365하여 age로 대체
- DAYS_EMPLOYED: abs() 후 로그 변환한 log_DAYS_EMPLOYED 로 대체
(양수 값은 고용되지 않은 상태를 의미함: 고용된 사람들의 중앙값으로 대체)
- employed_age 칼럼 생성: DAYS_BIRTH과 DAYS_EMPLOYED로부터 파생
- FLAG_MOBIL: 삭제
- work_phone, phone, email: 그대로
- occyp_type: null 값들은 income_type이 Pensioner 인 경우 occyp_type을 "retired"로 새로 지정하고 그 외 income_type 은 해당{income_type}_unanswered로 occyp_type 새로 지정 후 pd.get_dummies 처리
- family_size: 그대로
- begin_month: abs()
- credit





