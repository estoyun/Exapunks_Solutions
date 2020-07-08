# GOAL
~~~
File 200 contains exactly one number, N.
Create a new file in the outbox containing the numbers N through 0 in decreasing order.
When you are finished, delete file 200.
~~~

~~~
1. Create the specified file in the outbox.
2. Delete file 200.
3. Leave no trace.
~~~

# FILE
~~~
200 "9"
~~~

# SOLUTION
> ### XA
~~~
LINK 800
GRAB 200
COPY F T
WIPE
LINK 800
MAKE
MARK LOOP
COPY T F
SUBI T 1 T
TJMP LOOP
COPY T F
~~~

# COMMENT
> ### 파일 수정
~~~
WIPE : 들고있는 파일을 삭제한다.
~~~

> ### 분기
~~~
MARK L : 이 행은 L이라는 이름을 가진 레이블이 된다.
TJMP L : T 레지스터가 1(참)일 경우 L 레이블로 점프한다.
~~~

~~~
굳이 1이 아니더라도 T 레지스터에 0 이외의 아무값이나 들어가 있으면 L 레이블로 점프한다.
~~~
