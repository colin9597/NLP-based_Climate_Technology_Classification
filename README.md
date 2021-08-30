# <NLP-based_Climate_Technology_Classification>
[DACON] 자연어 기반 기후기술분류 AI 경진대회  
(2021.06.21. ~ 2021.08.16.)
- 팀원 : <code>김동현</code> <code>전광훈</code> <code>유경민</code>
- 리더보드 최종 순위 25등(상위 10%)  
  ![KakaoTalk_20210828_170854081](https://user-images.githubusercontent.com/80561963/131211272-72512112-fb39-44af-9fae-1d408500c5b5.jpg)
---

## 개발 환경
#### [개발 환경]
- 서버 : Colab
- CPU 2.20GHz 2코어
- 메모리 12GiB
- CUDA 11.2
- Ubuntu 18.04.5 LTS
- Python 3.7.11

#### [데이터 출처]
- 녹색기술센터 제공 [link](https://dacon.io/competitions/official/235744/data)
---

## Data
#### [train.csv]
- 기후기술분류 label 포함
- 심각한 불균형 데이터임.
- train.shape : (174304, 13)

#### [test.csv]
- 기후기술분류 label 미포함
- test.shape : (43576, 12)

#### [sample_submission.csv]
- sample_submission.shape : (43576, 2)

#### [labels_mapping.csv]
- label과 기후기술분류체계를 mapping 한 meta data
---

## Preprocessing
#### [형태소 분석기 선정] - kkma/komoran/hannanum/mecab/okt  
###### 1) 띄어쓰기가 제대로 되어있지 않은 문장  
  > mecab > kkma = komoran = okt > hannanum  
- 더욱 자세한 품사를 알고 싶다면 kkma 나 komoran
- 간단한 품사를 알고 싶다면 okt

###### 2) 오탈자 때문에 불완전한 문장  
- komoran 사용하는 것이 좋다.

###### 3) 속도 비교  
  > mecab > komoran > hannanum > okt > kkma
- mecab 이 압도적으로 빠르고, kkma가 압도적으로 느림

=> train 데이터에 띄어쓰기 문제나 오탈자가 없으므로 속도를 고려하여 **mecab**을 형태소 분석기로 선정

#### [피처 통합]
- 여러 피처 조합으로 성능을 비교했을 때, 대체로 '사업명', '과제명', '요약문_연구목표', '요약문_한글키워드' 피처의 성능이 좋았음.
- 처리 시간과 성능을 고려하여 '사업명'+'과제명'+'요약문_한글키워드'로 피처를 통합
- (파생변수 생성) train["data"] = '사업명 : ' + train['사업명'] + ', 과제명 : ' + train['과제명'] + ', 키워드 : ' + train["요약문_한글키워드"]  
  => 피처를 통합할 때, 따로 '사업명 :'과 같은 머리글 삽입 (→성능 향상)
