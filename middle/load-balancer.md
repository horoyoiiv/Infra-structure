


# Load Balancer  


## 1. 종류  
 네트워크 계층은 아래서부터  
 Physical - Data Link - Network - Transport - Session - Presentation - Application  
 

#### 1. L4 Load Balancer  
  * Transport Layer에서 동작한다.  
  * 이 계층에서는 **IP**, **Port** 를 다루기에 이 정보를 바탕으로 서버를 선택  
  

#### 2. L7 Load Balancer  
  * Application Layer에서 동작하며, HTTP 프로토콜까지 적용하여 서버를 선택  
  * 서버 선택을 위한 메타 정보를 HTTP header에 저장한다.  
  * 
  
 1. 쿠키를 활용  


## 2. 방식  


#### 1. Round Robin  


#### 2. Weighted Round Robin  
  * 클러스터를 구성하는 **노드 간 퍼포먼스의 차이가 있다면 성능이 우수한 서버에 load를 더 분산**시킬 수 있을 것.  
  * 라운드 로빈은 순차적으로 서버에 요청을 분산하는 것이라면  
  Weighted는 각 서버에 가중치를 부여한 후 가중치만큼의 요청을 분산한다.  
  
```
예) 라운드 로빈
서버 1 2 3 4 5 가 있다면 들어오는 요청을 다음과 같이 배분

1 2 3 4 5 1 2 3 4 5 1 2 3 4 5
```

```
예) 가중치 라운드 로빈
서버 1 2 3 4 5 가 있고 가중치가 
    1 3 2 1 1 이라면 다음과 같이 배분

1 [2 2 2] [3 3] 4 5 1 [2 2 2] [3 3] 4 5...
```
  
  






#### So.  
  * L4 로드 밸런서는 IP주소 + 포트 번호를 바탕으로 서버를 선택  
  * L7 로드 밸런서는 IP주소 + 포트 번호 + 패킷 내용을 바탕으로 서버 선택  
  

## Features  


#### 1. Sticky Sessions  

  * 기본적인 traffic의 분산 방식은 Round-Robiin일 것이다.  
  * Sticky session은 요청으로 들어오는 request의 IP 바탕으로 동일한 IP를 동일한 서버에 할당하는 것.  
  
```
Sticky session refers to the feature of many commercial load balancing solutions 
for web-farms to route the requests for a particular session
to the same physical machine that serviced the first request for that session.
```

  * sticky sessions can cause uneven load distribution across servers.  





#### 참고  


[d2 자료](https://d2.naver.com/helloworld/284659)  


  
