# novel_analysis_1
## 1. 문제정의
### 1. 웹소설에서 댓글의 역할과 중요성

소설은 과거부터 현재까지 많은 사람에게 여러가지 희로애락을 안겨준 좋은 유흥거리이다. 그중 웹소설은 기존 소설에 비해 더 가볍고 독자친화적인 성격을 띤 소설인데 기존의 소설이 프롤로그와 엔딩까지 한번에 주는 식이라면 웹소설은 한화씩 연재하는 방식을 가진다. 이런 연재방식에는 장단점이 존재 하는데 장점으로는 단편식 연재다 보니 매화 독자들의 반응을 살필 수 있는데, 웹소설은 매화 조회수에 따라 수입을 버는 상업적 소설이기 때문에 작품의 여론이 매우 중요하다. 작품의 여론이 나쁘다면 그에 비례하여 작품의 조회수도 빨리 내려가기 때문이다. 그렇기 때문에 여론을 파악하여 글의 방향을 조정할 수 있다는 사실은 매우 중요하다. 단점은 독자들이 여론을 이용하여 작가를 자신의 입맛에 맞는 소설을 쓰도록 쥐고 흔들려고 한다. 

### 2. 웹소설의 양산화

웹소설은 기존 소설에 비해 가볍고 직관적이기 때문에 전문 작가들뿐만 아니라 직장인, 학생, 주부 남녀 구분없이 누구나 쓸수 있다. 부업이 유행하고 있는 현대 사회에서 다른 부업들과는 달리 집에서 편하게 글만 쓰면 돼고 잘만된다면 거액의 돈을 벌 수 있는 웹소설을 쓰지 않을 이유는 없다. 그렇기 때문에 현 웹소설 시장을 너도나도 뛰어들다보니 소설들은 넘쳐나지만 퀄리티가 좋은 것들을 찾기가 힘들어졌다. <br/>

## 2. 데이터 들여다 보기

* 데이터 수집 기준 <br/>
댓글이 많은 소설들에서 1화부터 25화까지의 댓글을 수집하여 대략 30000만개의 데이터를 수집하고자 했습니다.<br/>

* 데이터  

|number|file_name|Comment|Date|
|------|---------|-------|----|
|1|검은 머리 미군 대원수 대체역사|"조범석 아르민 산신령 합작 레토나 ㅋㅋㅋ.심지어 약관 위배하고 조져버리다니 슬프다"|20240305|
|2|검은 머리 미군 대원수 대체역사|다시 왔습니다... 그립진 않습니다 대머리 듀오...|20240308|
|3|검은 머리 미군 대원수 대체역사|정주행 시작|20240312|
|.....|..........|.................|.........|
|27900|회귀수선전 무림|헉헉. 숨도 못쉬게 읽고 무아지경에 이르다니…|20230325|
|27901|회귀수선전 무림|존잼|20230326|
|27902|회귀수선전 무림|재밌어요|20230326|
|27903|회귀수선전 무림|서은현이 벤다|20230326|


총 9개의 소설에서 댓글을 수집하여 27903개 데이터를 수집했고 데이터는 데이터 번호, 소설의 제목과 장르, 댓글, 댓글 작성 날짜로 구성 돼있다.<br/>

![image](https://github.com/user-attachments/assets/ebbece09-fa20-4f51-96be-f44399d7c402)

### 1. 데이터 라벨링
* 데이터 추출 <br/>
총 27903개의 데이터중 3000개의 랜덤 데이터를 추출 하돼 원본 데이터의 소설간의 비율을 보존 한채 추출하기로 했다. <br/>
![image](https://github.com/user-attachments/assets/98b1dc0f-8d4f-4007-b373-2ed32e6e63c0)<br/>

* 긍부정 라벨링<br/>
긍정적인 내용의 댓글을 1 부정적인 댓글을 0 애매하거나 긍부정과 관련없는 댓글들을 2로 설정하여 3000개의 데이터의 라벨링을 진행했다.<br/>

|number|file_name|Comment|Date|label|
|------|---------|-------|----|-----|
|20601|전독시 퓨판|잘 보고 갑니다|20220821|1|
|19913|전독시 퓨판|잘 읽었습니다.|20240520|1|
|23278|전독시 퓨판|"즐감합니다!!건필하세요~"|20180120|1|
|20613|전독시 퓨판|잘읽었습니다. 건필하세요.|20190123|1|
|.....|..........|.................|.........|........|
|26916|회귀수선전 무림|빡웅 3회차때는 뭐였더라 마을 이장 죽이고 암살당했었나|20230426|2|
|26183|회귀수선전 무림|지인들 모두 성공했는데 고향 지구인 한명도 챙겨주지 않았네요|20230304|2|
|27427|회귀수선전 무림|진짜 잼있어요. 이런 진행이 마음에 듭니다.|20230326|1|
|27246|회귀수선전 무림|너무 억지로 둔재 조건 설정한듯|20230319|0|<br/>

### 2. 데이터 분석<br/>
데이터 분석에 앞서 모든 분석은 확실한 긍부정을 갖고 할 것이기 때문에 라벨링이 2인 애매한 항목들을 전부 제외하고 진행 할 것입니다.<br/>
* 소설별 긍부정비율과 평점간의 상관관계<br/>
평점이 높은 다는것은 독자들의 반응이 그만큼 좋았다는 것이고 부정적인 댓글들이 달리는 비율이 적다고 판단하였다. 그렇기 때문에 평점이 높은 작품과 긍부정 비율이 높은 작품의 흐름이 비슷할 것이라고 생각했다.<br/>
![image](https://github.com/user-attachments/assets/cdd1d3e6-c427-439a-b2a2-37905dae4398)
![image](https://github.com/user-attachments/assets/9ca50f60-1875-448b-801c-c5ea3e38db1c)<br/>

  * 두개의 그래프를 통해 평점의 높낮이와 상관없이 악플은 달린다는 것을 알 수 있었다.<br/>

  

* 장르별 긍부정 비율  <br/>
장르에 따라 독자들의 반응과 댓글들의 여론이 전부 다르다. 예를 들어 대체 역사물은 고증을 중요시해서 지키지 않으면 반응이 부정적이고 무협은 전통무협이 아니면 악플을 다는 등과 같이 장르별로 반응이 천차만별이다.
그래서 장르간 긍부정 비율을 살펴보려 한다.                                    
![image](https://github.com/user-attachments/assets/cc861417-348a-44e3-96ea-21c6821e9bb2)


  * 드라마 장르를 가진 작품들은 비교적 독자들이 반응이 유한것에 비해 무협을 쓰는 작가들은 다소 작품을 연재할때 고충을 겪을 것으로 보인다.
 
## 3. 모델 학습 및 검증<br/>

### 3.1 모델 학습

* 모델 학습 시 문제점<br/>
소설 댓글에는 명확한 긍부정 댓글들만 있는게 아니라 애매한 평, 소설의 내용에 관한 이야기 등등 여러가지 댓글들이 존재하는데 그 모든 항목들을 라벨 2로 설정하였다. 그 후 라벨링 결과 긍정은 1249개, 부정은 313개, 애매모호가 1438개 라벨링 2가 거의 반을 차지했다.
여기서 문제가 발생하는데 일단 첫번째 현재 모델의 목표는 긍부정 예측이기 때문에 라벨을 2개만 사용할 것인데 그러면 라벨2를 가진 모든 항들을 다 삭제해야 된다. 그렇게 되면 남는 데이터의 수는 1500개로 본래 3000개의 데이터의 반으로 줄어들어 학습후 모델의 정확도에 대한
신뢰성이 떨어진다. 두번째 현재 긍부정 비율이 1249:313으로 긍정의 비율이 압도적으로 높아 해당 모델을 학습시 나오는 정확도에 대한 신뢰도가 또 떨어진다.

* 모델 학습 방법<br/>
  해당 모델의 정확도의 신뢰도를 높이기 위해 몇가지 방법들을 사용 할 것이다.<br/>
  
  1. 학습 데이터와 검증 데이터를 나눠서 해당 모델의 과적합을 방지한다.
  2. f1를 사용하여 해당 모델의 정확도를 검증한다.
  3. 전체 데이터 셋에 대하여 모델을 사용하여 검증한다.

### 3.2 모델 학습 결과
 

  

![image](https://github.com/user-attachments/assets/36a9086d-109b-41bd-b368-4870703a8571)![image](https://github.com/user-attachments/assets/817c00df-3f92-4272-b4c2-b014c7bb8155)

위의 그래프에서 첫 번째는 학습 정확도와 검증 정확도의 변화, 두 번째는 학습 F1 점수와 검증 F1 점수의 변화를 나타냅니다. 이를 통해 모델의 성능이 에폭이 진행됨에 따라 향상되고 있음을 시각적으로 확인할 수 있습니다.

정확도 그래프<br/>
학습 정확도는 꾸준히 증가합니다.
검증 정확도는 약간의 변동이 있지만, 전반적으로 안정적입니다.<br/>

F1 점수 그래프<br/>
학습 F1 점수도 꾸준히 증가하며 모델이 학습 데이터에 대한 성능을 점진적으로 향상시킵니다.
검증 F1 점수는 비교적 안정적이나, 마지막 에폭에서 약간의 감소가 관찰됩니다. <br/>

이를 통해 모델의 학습이 성공적으로 진행이 됐다고 판단 할 수 있을 것 같다



  

  








