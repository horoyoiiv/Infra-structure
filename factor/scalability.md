

# Scalability  
  * 확장성  
  
  ![image](https://user-images.githubusercontent.com/62331555/78006320-d0d2cd80-7377-11ea-9645-46f60a590a43.png)  

## What  

  * 갑작스러운 서버의 **workload** 증가 시 이를 처리하기 위하여 서버의 용량과 성능을 증가시켜야 한다.  
  * Scalability는 **이러한 load 증가에 대하여 어떻게 반응할 것인가**에 대한 내용.  
  

## 종류  

#### 1. Scale-up (Vertical Scaling)  
  * 서버의 CPU나 RAM을 추가하는 등 서버 자체의 처리 능력을 향상시킴.  

[단점]
  * Hardware limit이 있다.  
  * Single Point of Failure의 위험이 있다.  

[장점]  
  * Consistency 측면에서 유리하다.  
  * IPC를 통한 컴포넌트가 통신이 빠르다.  


#### 2. Scale-out (Horizontal Scaling)  
  * 갑작스레 증가된 부하를 처리하기 위하여 서버 자체를 추가하여 성능을 향상시킴.  
  * 이 때, 서버는 여러 대가 되기 때문에 각 서버의 부하를 분산시키기 위한 **로드 밸런싱**이 필수적.  
  * middle-ware component로서, 로드 밸런서가 필요한 것.  
  

[단점]  
  * Data Inconsistency를 신경써야 한다.  

[장점]  
  * Resilent하다.  
  
  
  
