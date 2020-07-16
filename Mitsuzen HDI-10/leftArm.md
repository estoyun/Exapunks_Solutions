# GOAL
~~~
Read a value from the nerve connected to your central nervous system (CNS)
and relay it to the nerve connected to your arm (ARM),
clamping the value so that it never goes below -120 or above 50.
Repeat ad infinitum*.

*ad infinitum : "무한" 또는 "영원히"를 의미하는 라틴어 문구

Since this task takes place inside a network you control
- that is, your own body - it is not necessary to leave no trace.
Your EXAs should be written to operate indefinitely.

Note that #NERV is a hardware register, not a file.
You can use it directly in your code like any other register.
~~~
~~~
1. Relay all nerve signals as indicated. (0/30)
~~~

# HARDWARE REGISTER
~~~
CNS #NERV
ARM #NERV
~~~

# SOLUTION

> ### XA
~~~
LINK 800
MARK LOOP
COPY #NERV X

TEST X < -120
TJMP SMALL

TEST X > 50
TJMP BIG

COPY X M
JUMP LOOP

MARK SMALL
COPY -120 M
JUMP LOOP

MARK BIG
COPY 50 M
JUMP LOOP
~~~

> ### XB
~~~
LINK 800
@REP 4
LINK 1
@END

MARK LOOP
COPY M #NERV
JUMP LOOP
~~~

# COMMENT

> ### 값 수정
~~~
COPY R/N R : R/N을 R에 저장한다.
~~~

> ### 매크로
~~~
@REP N ... @END : 범위 내 명령어, 즉 ... 부분을 N회 복붙하게 된다.
~~~

> ### 분기
~~~
MARK L : 이 행은 L이라는 이름을 가진 레이블이 된다.
JUMP L : L 레이블로 점프한다.
TJMP L : T 레지스터가 1(참)일 경우 L 레이블로 점프한다.
       : 굳이 1이 아니더라도 T 레지스터에 0 이외의 아무값이나 들어가 있으면, L 레이블로 점프한다.
~~~

> ### 비교기
~~~
TEST R/N (< or > or =) R/N
~~~

~~~
두 R/N을 부등호 혹은 등호대로 비교하여, 참일 경우 1, 거짓일 경우 0을 T 레지스터에 저장한다.
레지스터에 저장된 문자열도 비교의 대상이 될 수 있으며, 각각의 비교 결과는 다음과 같다.

R/N(숫자)과 R/N(문자열)을 비교하면 항상 거짓(0)
~~~
