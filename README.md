# 📝 DaJobA

## ✔️ 팀원
| _이름_ | 노영준 | 엄현호 | 이재현 | 이정우 | 이경민 | 강현준 |
|:-----:|:----:|:-----:|:----:|:----:|:-----:|:----:|
| ___역할___ | 멘토 | AI | BE | Crawling | BE | FE |
| ___Github___ | <a href="https://github.com/youngjun-99"><img src="https://avatars.githubusercontent.com/u/83204523?v=4" width="64" height="64"></a> | <a href="https://github.com/umleeho1"><img src="https://avatars.githubusercontent.com/u/109669006?v=4" width="64" height="64"></a> | <a href="https://github.com/jjaebbi"><img src="https://avatars.githubusercontent.com/u/112852283?v=4" width="64" height="64"></a> | <a href="https://github.com/j-ra1n"><img src="https://avatars.githubusercontent.com/u/118893707?v=4" width="64" height="64"></a> | <a href="https://github.com/rudalsss"><img src="https://avatars.githubusercontent.com/u/122061889?v=4" width="64" height="64"></a> | <a href="https://github.com/unfl1"><img src="https://avatars.githubusercontent.com/u/130300481?v=4" width="64" height="64"></a>

## ✔️ 프로젝트 기간
- 2023.09 ~ 2023.12

## ✔️ 추진 배경
<div>
<img width="500" src="https://github.com/user-attachments/assets/5deab8a5-f2fe-48fe-a78b-4be547e49f77">
<img width="500" src="https://github.com/user-attachments/assets/148ede66-430c-4013-a1a4-e70592680ab9"><br><br>
</div>

- 20대 청년들에게서 발생하는 취업문제 : 원하는 양질의 일자리와 고용시장에서 요구하는 인적자원의 수준간의 심각한 차이가 발생하고 있다. <br>
- 국내 채용플랫폼 사용량은 지속적으로 증가하고 있지만, 이용자가 원하는 수준의 서비스를 제공하고 있지는 못하였다. <br>
- 채용플랫폼을 통해 수많은 채용정보를 얻을수는 있었지만 그 양이 너무 방대하여 분석이 어려움을 확인하였다. <br>

## ✔️ 프로젝트 목표
- 합격자소서 데이터로 학습한 AI를 통해 사용자의 개별 자소서를 분석하여 합격률이 높을 것으로 예상되는 채용공고를 선별해주는 ***사용자 맞춤형 채용플랫폼***을 구축한다. 
<img width="880" src="https://github.com/user-attachments/assets/bc209eef-5553-4ff9-8d9b-bcab4996d31e">

## ✔️ 시스템 설계도
<img width="880" src="https://github.com/user-attachments/assets/87b2ab6c-4657-437d-9f9b-bb481e20b6b1">

## ✔️ AI 모델 구축과정
<img width="600" src="https://github.com/user-attachments/assets/07800a24-673e-4ea0-b425-9c7d9b1ce112">

|단계|내용|이미지|상세설명|
|:-:|:-:|:-:|:-:|
|1| 기반 언어모델 : roberta | <img width="1200" src="https://github.com/user-attachments/assets/8d56a8d6-8e8e-48b1-9f0d-8e56767b4778"> | 뛰어난 성능지표를 보이는 언어모델 roberta의 large버전과 small버전을 모두 이용했다.|
|2| simCSE 지도학습으로 직무분야 학습 | <img width="1200" src="https://github.com/user-attachments/assets/02133c54-cac0-4e95-9dea-45c1b11f994c"> | 채용공고와 합격자소서 크롤링 데이터의 문장마다 dropout으로 서로다른 임베딩쌍을 생성하여 학습한다. <br> 같은 문장에서 유래한 두 임베딩은 가까워지도록 학습하고 다른문장의 임베딩들은 멀어지도록 학습한다. |
|3| simCSE 비지도학습으로 채용공고 매칭학습 | <img width="1200" src="https://github.com/user-attachments/assets/d66c0e06-1fad-4993-8850-29fe8396a08d"> | 채용공고와 이에 합격한 자소서의 문장들은 encoder를 거쳐 임베딩쌍으로 변환된다.<br> 이후 긍정인스턴스와 부정인스턴스로 구분하여 학습하며 유사도기반 매칭을 강화한다 |
|4| 문장유사도기반 매칭 알고리즘 | <img width="1200" src="https://github.com/user-attachments/assets/de8abf5e-0535-48da-b71b-cded2285e121"> | 사용자가 입력한 자소서의 문장과 채용공고 문장들을 모두 일대일로 비교하여 가장높은 유사도값(max)을 구한다. |
||| <img width="1200" src="https://github.com/user-attachments/assets/077e0672-e15d-43ef-8e8c-d7e4e1e00918"> | max유사도 값들을 평균내어 최종매칭점수를 도출한다. |
|5| 매칭알고리즘 강화 | <img width="1200" src="https://github.com/user-attachments/assets/a7ff76f1-245e-4c18-afd4-8555fc5081e1"> | 기존의 문장별 일대일 학습에서 매칭 정확도는 높았지만 소요시간이 매우 컸다. <br> 이를 해결하기 위해 주요업무 및 우대사항과 관련된 정보들로만 1차 매칭을 거치는 강화 알고리즘을 개발하였다. |
||| <img width="1200" src="https://github.com/user-attachments/assets/a722fff2-65e1-4a92-a663-d790d12fa695"> | 이에 따라 1건당 매칭시간은 대폭 감소시키면서 매칭 정확도는 여전히 유지할 수 있었다. |
|6| 동작방식| <img width="1200" src="https://github.com/user-attachments/assets/6b1549d9-8566-40cb-aa2c-396e95016f94"> | 사용자의 자소서가 등록 및 변경되는 경우, 새로운 크롤링 데이터가 유입되는 경우 분석시그널이 발생하여 AI가 구동된다. <br> 분석결과는 DB에 저장되어 제공된다. |


<br></br>
Backend <br>
API 명세서 : https://verdant-manicure-979.notion.site/DAJOBA-API-ec4ececd6f39476786ca72732d8ddb76?pvs=4 <br>
기능 정의서 : https://docs.google.com/spreadsheets/d/1XZoTWOw3ifeOBAzbPdCXyLfn3nto0Aot/edit#gid=948384303
