# 프로젝트1 : 차기 게임 개발을 위한 데이터 분석 (version2.0)

# 1. Overview

## 1.1. 배경과 목적
- 배경 : 한 게임회사 데이터 팀에 근무 중
- 목적 : **다음 분기에 어떤 게임을 설계해야 하는가?**
- 데이터 분석을 통해 대시보드를 만들고, 인사이트를 얻어 의사결정하고자 함 

## 1.2. 데이터 소개
- vgames2.csv : 2016년 까지의 게임 정보와 출고량을 나타내는 데이터셋
- 16598 rows × 9 columns

### Columns Description
- Name : 게임의 이름
- Platform : 게임을 구동하는 플랫폼 이름
- Year : 게임 출시 년도
- Genre : 게임의 장르
- Publisher : 게임 제작사
- NA_Sales : 북미 지역에서의 판매량
- EU_Sales : 유럽 지역에서의 판매량
- JP_Sales : 일본 지역에서의 판매량
- Other_Sales : 기타 지역에서의 판매량

## 1.3. 스킬셋
- pandas
- numpy
- matplotlib
- seaborn
- tableau

---
# 2. 데이터 전처리
- **총 판매량 50만 장 이상의 게임 데이터만 추출**
- 게임 이름이 유일한 데이터, 게임 이름이 중복되는(크로스 플랫폼 출시) 데이터 나눠서 전처리

## 2.1. 판매량
- 판매량 컬럼 값의 'M', 'K' 삭제 및 단위에 맞게 수정
- 총 판매량을 나타내는 'Total_Sales'컬럼 생성 후 전체 합산 값 저장

## 2.2. 연도
- 연도 값 이상치 발견 후 수정

## 2.3. 결측치 제거 및 대체
- 중요한 연도, 장르, 퍼블리셔 값은 가능한 정보를 검색하여 기입


---
# 3. 데이터 분석
- 데이터 시각화 및 분석은 태블로를 활용함
- 대시보드 : https://public.tableau.com/app/profile/yeeoonoo/viz/Project1_16856851500320/1

## 3.1. 지역에 따라서 선호하는 게임 장르가 다른가
- 각 지역 판매량을 기준으로 선호 장르 파악
- 연도를 고려하지 않은 이유 : 게임의 출시년도와 관계없이 게임이 재미있다면 사람들은 계속하여 소비함

### 분석 내용
- 북미, 유럽, 기타 지역 : 액션, 스포츠, 슈팅 장르가 판매량 전체의 50%정도 차지함
  - 북미 지역
![image](https://github.com/yeeoonoo/project1/assets/110115061/80c86dcf-50f5-4ebc-8a87-1eac55f3781b)
  - 유럽 지역
![image](https://github.com/yeeoonoo/project1/assets/110115061/32ee1f85-3f14-46ea-a07e-f00e7d4a0970)
  - 기타 지역
![image](https://github.com/yeeoonoo/project1/assets/110115061/df935926-97d5-4484-9ee0-6ed10b52a7bc)

- 일본 : 다른 지역과 달리 롤플레잉, 플랫폼 장르가 상당한 비중을 차지함
  ![image](https://github.com/yeeoonoo/project1/assets/110115061/b582c85e-e9f2-4f9a-8aef-5976c0a86b22)

- 전세계 게임 장르 선호도가 북미, 유럽, 기타지역과 유사한 양상을 보임
  - 전세계 판매량 각 지역 비중
![image](https://github.com/yeeoonoo/project1/assets/110115061/b74c0ddb-a7a0-43ea-95c6-312bffbcdcbb)
  - 전세계 게임 장르 선호도
![image](https://github.com/yeeoonoo/project1/assets/110115061/02528bdf-a92c-474f-83eb-bf5640944563)


### 결론 : 차기 개발 게임 장르는 액션, 스포츠, 슈팅 중에서 정하는 것이 좋을 것이라 판단함
- 일본 소비시장을 타겟팅하는 프로젝트가 아니라면 전체 시장을 고려하여 액션, 스포츠, 슈팅 장르의 게임을 개발하는 것을 제안  

## 3.2. 어떤 플랫폼으로 출시할 것인가
- 년도별로 출시한 게임들의 플랫폼을 분석
- 단일 플랫폼 독점 출시와 크로스 플랫폼 출시 중 더욱 판매효과가 큰 방식은 무엇인지 확인
- 플랫폼에도 트렌드가 존재하는지 확인

### 분석 내용
- Cross Platform
![image](https://github.com/yeeoonoo/project1/assets/110115061/2cd32a50-33bd-427b-bafc-5572fcb62955)
  - 추세를 보았을 때, 단일 플랫폼보다 크로스 플랫폼으로 출시하는 게임들이 많아지는 것을 확인할 수 있음
  - 또한 크로스 플랫폼으로 게임을 출시할 경우 단일 플랫폼 출시보다 판매량이 더 많을 가능성이 높음
    (발매한 지 오래되지 않은 최근 게임들의 판매량이 높은 경우가 많음)

- Preferred Platforms by Year
![image](https://github.com/yeeoonoo/project1/assets/110115061/9b222820-f932-4430-b74d-b598be3ec960)
  - 소니의 PS시리즈와 MS의 Xbox시리즈가 최신 트렌드를 주도하는 것을 확인할 수 있음.


### 결론 : 차기 개발 게임은 PS시리즈 와 Xbox시리즈 크로스 플랫폼으로 발매하는 것을 추천함

## 3.3. 판매 기준 상위 20개 게임들의 공통적 특징
- 상위 20개 게임의 발매 플랫폼과 장르를 확인

### 분석 내용
- Top 20 Games
![image](https://github.com/yeeoonoo/project1/assets/110115061/683f557a-b708-4bea-a541-34effd6cad77)

- 장르
  - 전반적으로 액션, 스포츠, 슈팅 장르의 게임이 많은 것을 확인할 수 있음
  - 다른 장르의 게임인 경우, 오랜 시간 꾸준히 사랑받아온 '슈퍼마리오', '테트리스', '포켓몬스터'의 브랜드 효과가 크다고 판단됨

- 플랫폼
  - PS시리즈와 Xbox시리즈 기반의 게임이 많은 것을 확인할 수 있음
  - 가장 보급률이 높은 PC로도 게임이 출시한 것을 확인할 수 있음
  - 게임 판매량이 높은 플랫폼 중 하나인 Wii의 경우, 판매량이 2009년을 기점으로 정체되어 10년부터 떨어지기 시작했으며 게임의 발매 수도 급감하였음

※ 슈팅 장르의 '콜오브 듀티', 액션 장르의 'GTA'의 경우, 다른 게임에 비해 비교적 최근에 발매했으며, 다양한 최신 기기는 물론 가장 보급률이 높은 PC를 포함한 크로스 플랫폼으로 출시하여 유저들의 접근성이 높음



---
# 4. 최종 결론
- **액션, 스포츠, 슈팅 장르로 글로벌 시장 공략**
- **XBOX, PS, PC 크로스 플랫폼 발매**
- **개인적인 추천 장르 : 밀리터리 또는 SF배경의 FPS**

## 해당 장르, 플랫폼 게임 예시
![image](https://user-images.githubusercontent.com/110115061/220880268-c2a5243d-717e-40bd-bd71-c9f89d3a825b.png)



---
# 5. 한계 및 개선점
- 데이터가 2016년 일부까지만 존재하여 최신 게임에 대한 정보가 다소 부족함
- 데이터에 판매량 이외에 게임에 대한 유저들의 반응도를 체크할 수 있는 지표가 없음. 댓글이나 평점 등의 정보가 있다면 트렌드와 선호도를 더 잘 파악할 수 있었을 것으로 생각함
- 게임 개발에 소요되는 비용이나 리소스에 대한 정보가 없어 수익성이나 효율 측면에서 문제를 분석할 수 없었음

