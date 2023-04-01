# What I Learned

## 공공데이터 EDA하기

### 1-1 데이터 읽어오기
* glob을 통해 데이터 파일 목록을 불러오고 반복문으로 합친다.

### 1-2 카페만 조회하기
* 1주차에 배웠던대로 df.loc을 이용해 '상권업종중분류명'이 '커피점/카페'인 항목만 모은다.

### 1-3 특정한 카페만 조회하기
* df.str.startswith와 df.str.contains 함수를 이용해 조건을 설정할수도 있다.
* startswith와 contains는 Pandas의 기능이다. 파이썬 내 다른 곳에서는 얌전히 in 연산자같은걸 쓰자. 다른 언어랑 헷갈리지 말고.
    * 일반 문자열에 contains 쓰다 에러떠서 검색해봤는데 [나만 헷갈린게 아닌가보다.](https://stackoverflow.com/questions/58773880/str-contains-pandas-returns-str-object-has-no-attribute-contains)

### 1-4 프랜차이즈 카페 조회해보기
* 카패 개수 새기랑 비율 계산은 순수 파이썬으로 했다. 그런 다음 DataFrame을 만들어 띄웠다.

### 1-5 시각화하기
* 위에서 계산한 카페별 개수를 파이차트로 표현한다.
* 비율은 알아서 계산해준다.

### 1-7? 인사이트
* 우리동네 카페 조회해서 3~5를 해봤다.

### 2-1 데이터 읽어오기
* 1주차에서 했던대로 csv 데이터를 불러온다.

### 2-2 결측치 확인하기
* Codes that print Missing Values: 1주차에 있던대로 isnull().sum()을 이용해준다.
* missingno 모듈 활용: matrix와 bar 두 종류가 있다. subplot을 이용하면 두개를 한 이미지로 합칠 수 있을것 같긴 한데 그냥 따로 plt.show()했다.
* 값이 예시랑 좀 다른데 사용한 데이터가 다른듯하다.
* 그나저나 저 모듈 이름 유래는 아무래도 포켓몬이 맞는것같다.

### 2-3 Distribution Check
* 2주차에서 미리 찾아봤던 for 이용하여 그래프 그리는 코드를 활용하였다.
* column 목록은 그냥 DataFrame을 list형으로 변환하니 바로 나왔다.
* plt.style.use('ggplot')을 이용하니 색이 괜찮아졌다.
* plt.subplots_adjust를 이용하여 차트 간 크기나 간격들을 조정할 수 있다.
    * 값에 따라 어떻게 변하는지 잘 모르겠어서 여러번 바꿔가며 예시랑 비슷하게 나오는 값으로 골랐다.
* 2주차에서는 쓰지 않았던 ax를 이번에 활용하였다.
* 반복분 밖에서 subplot은 12개를 생성했지만 실제 사용은 10개만 하므로 11번째 반복부터는 ax.remove()를 이용하여 없애준다.
* ax.tick_params(axis='x', rotation=30)를 이용하여 하단 글씨를 30도 회전해준다. 안그러면 겹처서 못알아본다.
* 왜인지는 모르겠지만 distplot와 countplot은 인자 형식이 다르다. 혼용하면 에러난다.
* 그리고 distplot은 deprecated 됐다고 뜨더라. 근데 검색 힌트에서 distplot이라 해서 그냥 썼다.
* 또 주어진 코드에서 matplotlib을 matploblib이라고 쓴 오타가 있어서 고쳐서 썼다.

### 2-4 Correlation Check
* 이건 푸는데 실패했다. 왜인지 네개밖에 안나온다. corr()을 빼면 아예 에러가 뜬다. 값에 숫자가 아닌게 포함돼서 그런 듯 한데 검색해도 답을 못찾겠다.
* 그나마 mask는 성공했다. numpy 써서 mask 만들고 인자로 넣으면 우상단이 사라진다. np.fill_diagonal(mask, False) 하면 예시처럼 가운데 1 대각선도 표시할 수 있다.
    * 가운데 대각선 표시하는거 찾는게 은근 힘들었는데 [여기](https://stackoverflow.com/questions/57414771/how-to-plot-only-the-lower-triangle-of-a-seaborn-heatmap)에서 찾았다.