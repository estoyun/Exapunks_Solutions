# GOAL
~~~
File 199 contains exactly two values: a keyword and a number.
Create a new file in the file in the outbox
and copy those two values to it,
swapping their order so that the number is first.
When you are finished, delete file 199.
~~~

~~~
1. Create the specified file in the outbox.
2. Delete file 199.
3. Leave no trace.
~~~

# FILE
~~~
199 "ECHO, 9780"
~~~

# SOLUTION
> ### XA
~~~
LINK 800
LINK 800
MAKE
COPY M X
COPY M F
COPY X F
~~~

> ### XB
~~~
LINK 800
LINK 799
GRAB 199
COPY F M
COPY F M
WIPE
~~~

# COMMENT

> ### 레지스터
~~~
M : 메시지 패싱용 레지스터. 하나의 EXA에서 값을 M 레지스터에 저장하려 하고,
    또다른 EXA에서 M 레지스터를 통해 값을 읽어내려 한다면,
    두 EXA간에 통신이 이루어져 값을 주고받을 수 있다.
    
    메시지 패싱은 두 EXA간의 1대1 통신이며, 통신이 완료된 시점에서 송신측과 수신측 모두 통신이 종료된다.
    송신측에서 특정 값을 여러 EXA에게 보내고자 한다면, 수신하는 EXA의 갯수만큼 송신 명령을 반복해야 한다.
    
    방향성이 존재해 수신자를 지정 가능했던 TIS-100와 달리, M 레지스터 통신의 경우 수신자를 지정할 수 없다.
    엉성하게 통신망을 구성할 경우 엉뚱한 EXA가 값을 수신한 채 통신이 종료되는 경우가 발생할 수도 있다.
    
    동일한 사이클에 2대 이상의 송수신이 이루어진다고 했을 때,
    한발 먼저 송신이나 수신 상태에 돌입하여 대기중이었다고 해서 먼저 통신이 완료된다고는 장담할 수 없다.
~~~  
> ### 파일 수정
~~~
MAKE : 새로운 빈 파일을 생성한다.
WIPE : 들고있는 파일을 삭제한다.
~~~

~~~
파일은 해당 EXA가 들고 있는 상태로 생성된다.
이미 파일 하나를 들고 있는 상태에서 MAKE 명령어를 실행하면 불가능한 명령이 된다.
~~~
