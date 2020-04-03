


## Keep-alive in HTTP  

  * HTTP/1.1부터 가능.  
  * HTTP 프로토콜에서의 header.  
  
## What  

#### 1. 연결에 대하여  

1) HTTP/1.1 이전, 클라이언트와 서버 간의 연결은 3-way handshake 후 데이터를 주고 받은 뒤 연결 종료  
서버의 입장에서는 특정 클라이언트에 dedicate할 수 없으니...  
**한번의 연결 후 연결 종료**  

2) 하지만 이러한 방식은 매번 3-way handshake와 4-way를 해야하기에  
네트워크의 traffic 증가 등 비용의 발생  

3) 이를 개선하고자, 최초에 연결된 TCP 커넥션을 재사용할 수 있도록 하는 것이 Keep-alive  



##  How   

#### 1. 클라이언트 ==> 서버  

1) 클라이언트가 요청을 보낼 때 아래와 같은 헤더를 추가  

```
Connection : Keep-Alive
```
서버에게 연결을 유지하고 싶다는 요청을 보내는 것 / 지켜준다는 보장은 없다.  


2) 클라이언트  <==== 서버

```
Connection : Keep-Alive
Keep-Alive : max=5, timeout=120
```

서버는 이에 응답하여  
**max** : 몇번의 데이터요청을 허용할지 결정  
**timeout** : (초 단위) 120초 동안 유지할지 결정  

  * max는 데이터가 한번 오고 가면 1씩 감소  
  
  



#### Example One  

* < Connection : Keep-Alive > 를 요청 헤더에 넣는다.  
* 서버는 timeout=5로 설정했다고 응답한다.  
* 요청이 없으면 5초 후에 서버가 연결을 종료시킨다.  

```
$ telnet pungjoo.com 80
Trying 121.124.124.74...
Connected to pungjoo.com.
Escape character is '^]'.

GET / HTTP/1.1
Host: pungjoo.com
Connection: Keep-Alive

HTTP/1.1 302 Moved Temporarily
Date: Tue, 15 Jan 2008 01:32:45 GMT
Set-Cookie: JSESSIONID=91569ADEF9D501B8071BD59D0DC04E82; Path=/
Location: http://pungjoo.com/servlet/com.pungjoo.blog2005.Action
Content-Type: text/html;charset=EUC-KR
Content-Length: 0
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive

// 5초 후
Connection to pungjoo.com closed by foreign host.



출처: https://b.pungjoo.com/entry/HTTP-11-Keep-Alive-기능에-대해 [pungjoo]
```


#### Example Two  
  * 5초 안에 요청을 더 보내면 max가 -1되며, 소캣은 그대로 사용한다.  

```
$ telnet pungjoo.com 80
Trying 121.124.124.74...
Connected topungjoo.com.
Escape character is '^]'.

GET / HTTP/1.1
Host: pungjoo.com
Connection: Keep-Alive

HTTP/1.1 302 Moved Temporarily
Date: Tue, 15 Jan 2008 01:36:26 GMT
Set-Cookie: JSESSIONID=2B3EE2FE56868BD9588A7B55C405974B; Path=/
Location: http://pungjoo.com/servlet/com.pungjoo.blog2005.Action
Content-Type: text/html;charset=EUC-KR
Content-Length: 0
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive

GET / HTTP/1.1
Host: pungjoo.com
Connection: Keep-Alive

HTTP/1.1 302 Moved Temporarily
Date: Tue, 15 Jan 2008 01:36:35 GMT
Set-Cookie: JSESSIONID=E4E3D9B9CFE3693DC5AFC3D6ABDE5564; Path=/
Location: http://pungjoo.com/servlet/com.pungjoo.blog2005.Action
Content-Type: text/html;charset=EUC-KR
Content-Length: 0
Keep-Alive: timeout=5, max=99
Connection: Keep-Alive

Connection to pungjoo.com closed by foreign host.



출처: https://b.pungjoo.com/entry/HTTP-11-Keep-Alive-기능에-대해 [pungjoo]
```


## So  

  * HTTP/1.0에 비하여, HTTP/1.1에서는 Default가 [Connection : keep-alive]  
  










