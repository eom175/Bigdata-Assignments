# 빅처응 과제 저장소

빅데이터 관련 주차별 과제를 정리한 저장소입니다.
실습은 주로 Google Colab + PySpark 환경에서 진행했습니다.

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

### 3주차 - Colab 3 링크 과제

- 제출본은 로컬 ipynb 대신 Colab 링크 파일(`.webloc`) 형태로 보관
- Colab 링크: <https://colab.research.google.com/drive/1m4Y-FdUq79wAA7te-o8Mx6Gq0WKRsuSj>
- 로컬 저장소에는 링크 파일만 있어 세부 코드/분석 내용은 해당 Colab 노트북에서 확인 가능

### 4주차 - Colab 4 링크 과제

- 제출본은 로컬 ipynb 대신 Colab 링크 파일(`.webloc`) 형태로 보관
- Colab 링크: <https://colab.research.google.com/drive/15OMp8TaBrVAOhrO7ooOT2h7AQXT8guUK>
- 로컬 저장소에는 링크 파일만 있어 세부 코드/분석 내용은 해당 Colab 노트북에서 확인 가능

## 비고

- `.webloc` 파일은 macOS 웹 바로가기 파일입니다.
- 노트북은 Jupyter/Colab 환경에서 확인할 수 있습니다.
