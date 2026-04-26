# awesome-conlanging

## Phonetics 음성학

### Source-Filter Model 소스-필터 모델
- 목소리는 성대의 원음(source)이 성도(vocal tract - 인두, 구강, 비강)를 지나며 filter된 것임

#### Harmonics 배음
- 400Hz로 목소리를 내면 그 배수인 800Hz, 1200Hz, 1600Hz, ... 성분도 소리에 포함됨

#### Formant 포먼트
- 

## Phonotactics 음소배열론

### Maximal Onset Principle 최대 음절 초성 원칙
- 자음이 앞 음절의 종성보다 뒷 음절의 초성에 붙는 경향
- 예(영어):
  - Reply [rɪ.plaɪ]
  - Admit [əd.mɪt]
    - 영어에는 /dm/ 초성이 없기 때문에, /d/가 앞 음절의 종성으로 남는다.

### Sonority Sequencing Principle 공명도 배열 원칙
- 초성에서는 공명도가 상승하고, 종성에서는 공명도가 하강해야 함
- 예외: 인구어의 /s/
  - Speak [spik]
    - 초성에서 s->p로 공명도 하강
- 공명도 척도
  - ptk < sfz < mn < lr < wj < iu < eo < a

## 기타

### Markov Chain 마르코프 체인
- 코퍼스에서 각 n-gram의 개수를 세고, 얻어낸 분포를 바탕으로 단어 또는 문장을 랜덤하게 생성
- 예:
  - 시카노코 https://youtu.be/Xkq13ZthmA0
    - しかのこのこのここしたんたん
    - ```
      し -> か : 1
      か -> の : 1
      の -> こ : 3
      こ -> の : 2
      こ -> こ : 1
      こ -> し : 1
      し -> た : 1
      た -> ん : 2
      ん -> た : 1
      ん -> 끝 : 1
      ```
    - ```
      し
        -> か : 50%
        -> た : 50%

      か
        -> の : 100%

      の
        -> こ : 100%

      こ
        -> の : 50%
        -> こ : 25%
        -> し : 25%

      た
        -> ん : 100%

      ん
        -> た : 50%
        -> 끝 : 50%
      ```
  - 이름 생성기 https://www.samcodes.co.uk/project/markov-namegen/

## 추천 소프트웨어 (무료 오픈소스)

### 데이터 분석

#### Jamovi
- https://www.jamovi.org/
- 데이터를 가지고 가설을 검증할 때.
- GUI 기반. 코딩 필요 없음.
- 간단한 스크립트 적용 가능.
- 가설에 따라 아래 테스트 돌리면 p값이 나옴.
  - 이 분포의 평균이 x인가?
    - 정규분포일 때: One-sample T-test
    - 아닐 때: Wilcoxon signed-rank test

  - 두 집단의 평균이 서로 다른가?
    - 정규분포일 때: Independent two-sample T-test
    - 아닐 때: Mann-Whitney U-test

  - 동일 집단의 전/후 평균이 달라졌는가?
    - 정규분포일 때: Paired-sample T-test
    - 아닐 때: Wilcoxon signed-rank test

  - 세 집단 이상의 평균이 서로 다른가?
    - 정규분포일 때: One-way ANOVA
    - 아닐 때: Kruskal-Wallis test

  - 두 변수 사이에 상관관계가 있는가?
    - 정규분포일 때: Pearson correlation
    - 아닐 때: Spearman correlation

  - 범주형 변수 간에 연관이 있는가?
    - 일반적인 경우: Chi-square test
    - 표본 수가 적을 때: Fisher's exact test

  - 이 분포가 정규분포인가?
    - 시각적으로 확인할 때: Q-Q plot, Histogram
    - 통계적으로 검정할 때 (표본이 적을 때): Shapiro-Wilk test
    - 통계적으로 검정할 때 (표본이 많을 때): Kolmogorov-Smirnov test

#### Quarto
- Jupyter Notebook의 상위호환 버전
