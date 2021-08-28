# <NLP-based_Climate_Technology_Classification>
[DACON] 자연어 기반 기후기술분류 AI 경진대회  
(2021.06.21. ~ 2021.08.16.)
- 팀원 : <code>김동현</code> <code>전광훈</code> <code>유경민</code>
- 리더보드 상위 10%  
  ![KakaoTalk_20210828_170854081](https://user-images.githubusercontent.com/80561963/131211272-72512112-fb39-44af-9fae-1d408500c5b5.jpg)
---

## 개발 환경
#### [개발 환경]
- 서버 : Colab
- Ubuntu 18.04.5 LTS
- Python 

#### [데이터 출처]
- 녹색기술센터 제공 [link](https://dacon.io/competitions/official/235744/data)
---
## Data
데이터 csv 파일은 공유하지 않음.
#### [train.csv]
- 기후기술분류 label 포함
- train.shape : (174304, 13)

#### [test.csv]
- 기후기술분류 label 미포함
- test.shape : (43576, 12)

#### [sample_submission.csv]
- sample_submission.shape : (43576, 2)

#### [labels_mapping.csv]
- label과 기후기술분류체계를 mapping 한 meta data
