


# Load Balancer  





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


  
