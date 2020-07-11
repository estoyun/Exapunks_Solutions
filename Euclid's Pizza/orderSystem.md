# GOAL
~~~
Append your order (file 300) to the end of the order list (file 200).
~~~
~~~
1. Append your order to the end of the order list.
2. Leave no trace.
~~~

# FILE
~~~
300 "605, EDDY ST #801, MEDIUM, CHEESE, EXTRA CHEESE, ANCHOVIES"
200 "1883 JUNIPER ST #1835, LARGE, CHEESE, MUSHROOMS, ANCHOVIES, 468 10TH ST APT 2333, EXTRA LARGE, CHEESE, ONIONS,
     PEPPERONI, 342 BUSH ST #2, LARGE, CHEESE, EXTRA CHEESE, PEPPERONI"
280 ""
281 ""
~~~

# SOLUTION

> ### XA
~~~
GRAB 300
@REP 5
COPY F M
@END
~~~

> ### XB
~~~
LINK 800
GRAB 200
SEEK 9999
@REP 5
COPY M F
@END
~~~

# COMMENT

> ### 파일 수정
~~~
SEEK R/N : 파일 내의 커서를 앞(양수),뒤(음수)로 R/N의 숫자만큼 이동한다.
~~~

~~~
F 레지스터를 통해 파일 내의 값을 참조할 때마다 커서가 자동으로 뒤의 값으로 이동하므로,
이를 다시 재위치 시키기 위해 자주 사용된다.
~~~

~~~
-9999, 9999같이 한없이 큰 값을 입력시켜 파일의 제일 앞, 제일 뒤로 커서를 이동시키는 것도 가능하다.
~~~

> ### 매크로
~~~
@REP N ... @END : 범위 내 명령어, 즉 ... 부분을 N회 복붙하게 된다.
~~~

> ### 피자 먹고 싶다.
