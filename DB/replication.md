


# Replication  
  * Replication : (복사) 하나의 데이터베이스에 대한 여러 복사본 데이터베이스를 만드는 것.  
  

## What?  
  * 동일한 데이터를 저장하는 Slave라는 데이터베이스를 만든다.  
  
![image](https://user-images.githubusercontent.com/62331555/78117013-178bfa80-7440-11ea-9ff6-659604065137.png)   

#### 일반적으로 하나의 Master와 여러 개의 Slave로 이루어진 구조 속에서 ReadOnly인 Slave 노드들은 Application Server의 Select Query를 전담마크.  
  * Write이 가능한 하나의 Master 노드는 데이터가 업데이트되면 이를 Slave에게 알려준다.  
  
  * 그렇다면 Slave와 Master 간의 **데이터 동기화**는 어떻게 수행될까? HOW?  
  
  
  
##### Summary : DB를 복사하는 것이긴 한데... Writable Master DB와 ReadOnly Slave DB로 구성한다.  


## Why?  

  * Application server에서는 대게 DB에 대한 Select query가 주어진다.  
![image](https://user-images.githubusercontent.com/62331555/78117062-24a8e980-7440-11ea-8715-94ea3608d94e.png)  

  * 요청이 많아질수록 하나의 DB가 처리하게 되는 부하가 심해진다.  
  * 이를 해소하기 위하여 **select query만 전담하는 slave**를 만들 수 있다.  
  
  * Master server는 데이터의 수정 작업을 수행하고, Slave는 그 결과를 그대로 가져와 복사본을 저장.  
  
  
#### 1. Scale-out Solution이 될 수 있다.  
#### 2. Analytics : 서비스에 영향을 미치지 않고 데이터 분석 가능.  
  서비스를 제공하는 서버는 그대로 동작하고, 분석은 Slave 노드를 대상으로 수행하면 되니까!  
  
#### 3. 지리적 격차 감소 : Replication 서버를 지리적으로 Master와 User 사이에 배치하여 Latency 향상 도모.  

#### 4. SELECT Query 성능 향상 = Master 서버의 부하 분산  

 * Slave 노드가 Query의 대부분을 차지하는 Select 조회를 전담마크하여라...  
 
![image](https://user-images.githubusercontent.com/62331555/78118518-165bcd00-7442-11ea-912c-3d7875239a4c.png)  



## How  



## So ?  

#### 1. DB의 부하를 분산시킬 수 있다.  




[Ref] https://jins-dev.tistory.com/entry/Database-Replication-%EC%A0%84%EB%B0%98%EC%97%90-%EB%8C%80%ED%95%9C-%EC%9D%B4%ED%95%B4  
[Ref] https://nesoy.github.io/articles/2018-02/Database-Replication  
[Ref] https://www.geeksforgeeks.org/data-replication-in-dbms/  







