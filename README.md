# 빅처응 과제

빅데이터 관련 주차별 과제를 정리한 저장소.
실습은 주로 Google Colab + PySpark 환경에서 진행.

## 파일 구성

- 1주차: `2021203052_엄지용_1차과제.ipynb`
- 2주차: `KW_MMDS_Colab_2.ipynb`
- 3주차: `KW_MMDS - Colab 3.ipynb의 사본.webloc`
- 4주차: `KW_MMDS - Colab 4.ipynb의 사본.webloc`

## 주차별 상세 작업 내역

### 1주차 - WordCount in Spark

- Spark/Colab 실행 환경 구성 및 Google Drive 연동
- `pg100.txt`(셰익스피어 전집) 데이터 로드
- 대문자를 소문자로 변환한 뒤, 알파벳(`a`~`z`)으로 시작하는 단어만 필터링
- 단어 첫 글자 기준 등장 횟수 집계 후 알파벳 순 정렬 (`RDDs1`)
- `2641-0.txt`(A Room With A View) 데이터 로드
- 소문자 `c`로 시작하는 단어만 추출해 빈도 집계
- 빈도 내림차순 상위 10개를 형식에 맞춰 구성 (`RDDs2`)

### 2주차 - Frequent Pattern Mining in Spark

- Instacart 데이터셋(`products.csv`, `order_products__train.csv`) 로드
- `orders`와 `products`를 조인해 주문별 상품명 트랜잭션 생성
- FP-Growth 모델 학습 (`minSupport=0.01`, `minConfidence=0.5`)
- 빈발 항목집합 개수와 연관 규칙 개수 산출 (`num_freqItemsets1`, `num_associationRules1`)
- 가장 자주 등장하는 단일 품목 추출 (`most_freqItem`)
- `minSupport=0.001`로 재학습 후 결과 비교 (`num_freqItemsets2`, `num_associationRules2`)
- 최종 연관 규칙을 confidence 내림차순으로 정렬 (`associationRules`)

### 3주차 - K-Means & PCA

- Breast Cancer Wisconsin 데이터셋을 불러와 Spark용 feature 벡터로 변환
- 원본 feature에 대해 K-Means(`k=2`, `seed=1`) 군집화 수행
- Silhouette score 계산으로 군집 품질 평가
- 예측 클러스터와 정답 레이블을 비교해 올바르게 군집화된 데이터 수 계산
  - 클러스터 라벨 뒤집힘(0/1 swap) 가능성을 고려해 최대 일치 개수로 평가
- PCA(`k=2`)로 차원 축소 후 2차원 좌표 생성
- 차원 축소 데이터에 다시 K-Means를 수행하고 Silhouette score 재평가
- 아래 2가지 산점도 시각화 수행
  - PCA 공간에서 클러스터 예측 결과 시각화
  - PCA 공간에서 실제 레이블 기준 시각화
- Colab 링크: <https://colab.research.google.com/drive/1m4Y-FdUq79wAA7te-o8Mx6Gq0WKRsuSj>

### 4주차 - Collaborative Filtering (ALS)

- MovieLens 100K 기반 데이터(`MovieLens.training`, `MovieLens.test`, `MovieLens.item`) 로드
- 훈련/테스트 평점 수와 전체 영화 수를 계산해 데이터 규모 확인
- Spark MLlib의 ALS(Alternating Least Squares)로 추천 모델 학습
  - `userCol=user_id`, `itemCol=item_id`, `ratingCol=rating`
  - `coldStartStrategy=drop`, `seed=2025`
- 테스트셋 예측 결과로 RMSE 계산 및 성능 평가
- 학습된 모델을 사용해 `user_id > 930` 사용자 대상 Top-10 영화 추천 생성
- 추천 결과를 사용자별 예측 평점 내림차순으로 정렬해 출력
- Colab 링크: <https://colab.research.google.com/drive/15OMp8TaBrVAOhrO7ooOT2h7AQXT8guUK>

## 비고

- `.webloc` 파일은 macOS 웹 바로가기 파일입니다.
- 노트북은 Jupyter/Colab 환경에서 확인할 수 있습니다.
