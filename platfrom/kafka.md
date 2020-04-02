

## Kafka  


## What  
  * 카프카는 pub-sub 기반의 분산 메세징 시스템. (정도로 현재 이해했다.)  
  * 물론 그 기능이 다채로운 만큼 한 줄로 표현할 수는 없고, 사람마다 다르게 표현할 것이다.  
  

### 1. 분산 스트리밍 플랫폼  
  * 공식문서에서는 카프카를 다음과 같이 정의한다.  
  Kafka is a **distributed streaming platform**.  
  
  * 이를 아래의 도식으로 이해해보자.  
  
  ![image](https://user-images.githubusercontent.com/62331555/78275320-6cb53280-754c-11ea-8784-9ef0ede79c9b.png)  
  [출처](http://wiki.gurubee.net/pages/viewpage.action?pageId=33752042)  
  
 #### 1. 먼저 streaming  
  
  1.1. pub-sub 기반이기에  
  메세지를 카프카에 보내는 publisher와  
  카프카로부터 메세지를 소비(수신)하는 consumer가 있다.  
    
  1.2. 이 둘 사이의 메세지를 중계하는 역할을 하는 것이 kafka가 된다.  
  
  1.3. 그렇기에 message가 문자 그대로 streaming 되는 것이기에, Kafka는 데이터에 대한 **스트리밍**을 제공하는 것.  
  
  1.4. **데이터 파이프라인을 만들 수 있다!**  
  
####  2. 그 다음 Distributed 와 Platform  
  
  2.1. Kafka는 클러스터로 동작한다.  
  (클러스터란 여러 서버의 집합체로 이해?)  
  
  2.2. 그래서 위의 그림을 보면 Kafka Cluster 라는 큰 네모 안에 Kafka Broker가 3개 있다.  
  
  2.3. 즉, 이 3개의 broker가 **분산**하여 데이터를 처리하기에 Distributed  
  
  2.4. 이러한 Broker가 뛰어놀 수 있는 환경을 제공하기에 Platform  
  
  
  

  
### 2. Broker 로서의 동작    
  * Broker란 중개인이란 의미로, producer와 consumer 간의 메세지를 **중개**  
  
#### 1. Cluster 단위의 실행  
 * broker 서버가 하나만 실행되어도 cluser로서 실행.  
 



### 3. 특징  


#### 1. Loose coupling  
  * 우선 느슨한 결합은 카프카만의 특징은 아니다.  
  publisher-subscriber 모델에서의 메세지는 중간에 일종의 메세지 큐를 두고  
  pub은 메세지 큐를 향해 메세지 전송  
  sub은 메세지 큐에서 메세지 수신  
  을 통해 pub-sub 간의 의존성 제거  
  
#### 2. Scalability  
#### 3. Fault Tolerant  
#### 4. High Availability
  * 위의 세가지 특징은 하나로 묶어서 이해했다.  
  
  1) Kafka는 언급했듯 **클러스터**로서 동작한다.  
  2) 아까 본 그림에선 브로커가 3대였지만, 4대 5대 .... Scale-out이 용이  
  3) 이는 Falut-tolerant로 이어지고, 다시 HA로 이어진다.  
  
  
  





### 더 공부해야 할 것  

1. 카프카에서의 파티션  
2. 주키퍼  [what](https://tjsdud4634.tistory.com/1)  






















## Ref  


[그루비](http://wiki.gurubee.net/pages/viewpage.action?pageId=33752042)  
[참고2](https://engkimbs.tistory.com/691)  
[굿굿](https://soul0.tistory.com/499)  


