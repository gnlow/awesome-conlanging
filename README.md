# awesome-conlanging

## Phonetics 음성학

### Source-Filter Model 소스-필터 모델
- 목소리는 성대의 원음(source)이 성도(vocal tract - 인두, 구강, 비강)를 지나며 filter된 것임

#### Harmonics 배음
- 400Hz로 목소리를 내면 그 배수인 800Hz, 1200Hz, 1600Hz, ... 성분도 소리에 포함됨

#### Formant 포먼트
- 성도에서 원음의 특정 주파수 대역은 걸러내고 다른건 살리는데, 그 중 살려놓는 주파수 대역
- 포먼트들을 주파수 낮은 순으로 F1, F2, F3, ...라고 부름
- 모음에 따라 포먼트가 결정되며, F2를 x축, F1를 y축으로 해서 그리면 모음사각도랑 같은 모양으로 나옴
- 참고 이미지: https://www.researchgate.net/figure/F1-and-F2-of-some-IPA-vowels-1_fig1_320280448

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

## Typography 타이포그라피

### Metafont 메타폰트
- 직접 베지어 곡선으로 외곽선 그리는 대신, 펜과 펜의 경로를 수식으로 정의해서 글자를 그리는 프로그램
- 1980년대에 개발됨. 개인적으로 시대를 너무 앞서가서 실패했다고 생각합니다.

### Continuity 연속성
- 곡선이 얼마나 아름다운/부드러운지 어떻게 알 수 있을까?
- 이 주제에 대해서는 Freya Holmér 씨의 전설적인 영상 "The Continuity of Splines"을 꼭 보시기 바랍니다.
  - https://youtu.be/jvPPXbo87ds
  - 1시간 짜리인데 재미있어서 순식간에 지나갑니다.

### Spline 스플라인
- 점이 주어졌을 때, 어떻게 가장 아름다운 곡선을 그릴 수 있을까?

#### Bezier 베지에
- 현대 벡터 그래픽의 lingua franca
- Adobe Illustrator, Figma 등 거의 모든 벡터 툴에서 사용 가능
- 간단한 다항식으로 정의됨

#### Spiro
- https://levien.com/spiro/
- 아주 아름답지만 자유도가 적은 스플라인
- Raph Levien 씨가 2009년에 개발함
- FontForge, Inkscape에서 사용해볼 수 있음

#### Hobby's Spline
- https://www.jakelow.com/blog/hobby-curves
- Spiro보다는 좀 덜 아름답지만 Bezier로 변환하기 좋음
- Metafont에서 사용됨

## 추천 소프트웨어

### 데이터 분석

#### Jamovi
- https://www.jamovi.org/
- 데이터를 가지고 가설을 검증할 때
- GUI 기반. 코딩 필요 없음
- 간단한 스크립트 적용 가능
- 가설에 따라 아래 테스트 돌리면 p값이 나옴
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
- Python으로 데이터 분석/시각화 하고 싶을 때

### 프로그래밍 언어

#### Prolog (DCG)
- https://php.energy/trealla.html
- 번역기 만들고 싶을 때
- (엄청 재밌어 보이지만 쓸만한거를 만들어 내기는 뭔가 쉽지 않음...)
- 다른 언어처럼 한->영, 영->한 이렇게 함수 두개를 만드는게 아니라, 한<->영 규칙 하나만 작성해서 양방향 번역 가능
```prolog
translate(Korean, English) :-
    phrase(sentence(E), Korean),
    English = E.

sentence(English) --> 
    subject(S), 
    object(O), 
    verb(V),
    { flatten([S, V, O], English) }.

subject(i) --> [나는].
subject(he) --> [그는].

object([an, apple]) --> [사과를].
object([the, book]) --> [책을].

verb(eat) --> [먹는다].
verb(reads) --> [읽는다].
```
```prolog
?- translate([나는, 사과를, 먹는다], English)
  English = [i,eat,an,apple]
```
```prolog
?- translate(Korean, [he, reads, the, book]).
  Korean = [그는,책을,읽는다]
```
- 이런 식으로 생성 가능한 모든 문장을 나열하는 것도 가능
  ```prolog
  ?- translate(K, E).
    K = [나는,사과를,먹는다], E = [i,eat,an,apple]
  ;  K = [나는,사과를,읽는다], E = [i,reads,an,apple]
  ;  K = [나는,책을,먹는다], E = [i,eat,the,book]
  ;  K = [나는,책을,읽는다], E = [i,reads,the,book]
  ;  K = [그는,사과를,먹는다], E = [he,eat,an,apple]
  ;  K = [그는,사과를,읽는다], E = [he,reads,an,apple]
  ;  K = [그는,책을,먹는다], E = [he,eat,the,book]
  ;  K = [그는,책을,읽는다], E = [he,reads,the,book].
  ```
