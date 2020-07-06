# GOAL
~~~
Add the first two values of file 200,
multiply the result by the third value,
and then subtract the fourth value.
Append the result to the end of the file and then move it to the outbox.
~~~

~~~
1. Append the correct value to the end of file 200.
2. Move file 200 to the outbox.  
3. Leave no trace.
~~~

# FILE
> ### XA
~~~
200 "72, 52, 4, 60"
~~~

# SOLUTION
~~~
LINK 800
GRAB 200
COPY F X
ADDI X F X
MULI X F X
SUBI X F X
COPY X F
LINK 800
DROP
HALT
~~~

# COMMENT

> ### 레지스터
~~~
F : 해당 EXA가 들고있는 파일에 접근하는 레지스터.
    해당 파일에 저장된 값을 읽어올 수도, 값을 입력할 수도, 삭제할 수도 있다.
    어떠한 식으로든 F 레지스터를 통해 값을 읽어오거나 파일의 값을 고쳐쓸 경우, 파일 속 커서가 다음 위치로 자동으로 이동한다.

X : 가장 무난하게 사용 가능한 저장소.
    한번 저장된 값은 나중에 덮어쓰지 않는 이상 계속 유지된다.
~~~

> ### 값 수정
~~~
EXA가 처리할 수 있는 값의 절대값은 9999를 넘을 수 없다.
다섯자리 이상을 수동으로 저장하려 한다면 에러로 인해 실행 자체가 불가능하고,
연산 결과값이 다섯자리 이상이 된다면 결과값은 9999로 클리핑된다.
~~~

~~~
COPY R/N R : R/N을 R에 저장한다.
ADDI R/N R/N_2 R : R/N에 R/N_2를 더하여 R에 저장한다.
SUBI R/N R/N_2 R : R/N에 R/N_2를 빼서 R에 저장한다.
MULI R/N R/N_2 R : R/N에 R/N_2를 곱하여 R에 저장한다.
~~~
