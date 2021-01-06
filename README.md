# The Blue House National Petition bot

<br/>
<br/>
<br/>

#### 프로젝트 목적

<br/>

- 국민 청원을 활성화 시키고자 합니다.     

- 관심 있는 청원에 대하여 지속적인 관심을 유도하고자 합니다.

- 동일 주제의 여러 청원의 글을 하나로 모으고자 합니다.

   = 이와 같은 목적을 **자동 뉴스 봇** 으로 구현하고자 합니다.       

<br/>
<br/>

#### 프로젝트 진행

<br/>

1. 데이터 수집

2. 데이터 전처리

3. 유사 청원 추출 기능 생성

4. 자동 뉴스 봇 알고리즘 구축

5. wordcloud기반의 시각화 및 뉴스 기사 생성

(해당 github 저장소에는 제가 담당했던 4, 5번 과정에 대한 코드 설명을 담았습니다.)

<br/>
<br/>

#### 사용 Tool

<br/>

- 언어 : Python

- 데이터 수집 : beautifulsoup4, selenium

- 데이터 전처리 : pandas, konlpy, hanspell

- 뉴스 생성 알고리즘 : TF-IDF, word2vec

- 데이터 시각화 : wordcloud

<br/>
<br/>

#### 프로젝트 설명

<br/>

- 2017.08.19 ~ 2020.01.31 까지의 국민청원, 584,666개 글 중, 비공식 청원을 제외한 나머지 440,958개 글 웹 크롤링

- 복지, 사회, 스포츠, 경제와 같은 키워드별 주제를 선정

- 키워드 주제와 청원의 유사성을 TF-IDF와 Cosine 유사도 기반으로 계산하여 가장 유사하며 청원 동의 수가 많은 글을 추출

- 추출된 청원 글을 자동 뉴스 형태로 만들어 배포

<br/>
<br/>

#### 자동 뉴스 봇 알고리즘 흐름

<br/>

= 청원 글의 핵심 문장을 추출 후, 기사 글 빈칸에 삽입하는 방식으로 진행<
  (핵심 문장이 아닌, 핵심 단어로 추출할 경우, 해당 청원 글이 주제에 대한 찬성인지, 반대인지 파악하기 힘듦)

순서

1. 내용이 들어갈 빈칸을 둔 채, 고정된 기사 형식의 글을 생성

2. 중복 데이터 제거, 불용어 처리, 품사 태깅 작업 수행

3. '부탁합니다.', '청원합니다.', '바랍니다.'와 같은 요청어미로 구성된 청원 단어장 생성

4. 각 단어에 TF-IDF 가중치를 부여한 후, 단어 구성에 따른 문장 가중치 합산 계산

5. 청원 단어장에 해당하는 문장에 대하여 추가 가중치 부여

6. 가중치를 기준으로 순위를 부여하고, 상위 문장을 핵심 문장으로 선정

7. wordcloud와 함께 뉴스 기사 배포

<br/>
<br/>

#### 프로젝트 결과

<br/>

- 주제 키워드별, 유사 청원에 대하여 가장 동의 수가 많은 글을 자동 뉴스를 통해 집중적으로 배포할 수 있습니다.
- 이를 통해, 동일 주제에 대한 여러 청원 글의 집중도를 하나로 모을 수 있는 계기를 마련할 수 있다고 생각합니다.

- 자동 뉴스 알고리즘의 경우, 하나의 청원 글에, 2가지 이상의 주제가 담기는 경우를 제외하고 글의 주제와 맞는 문장을 추려내는 것을 확인했습니다.
- 다만, 추출된 핵심 문장의 서순이 어색하거나, hanspell을 통해 맞춤법을 검사한다 하더라도 맞춤법이 어긋나는 문제를 보유하고 있습니다.
- 이에 대해, 추가적인 개선 작업이 필요하다고 생각됩니다.








