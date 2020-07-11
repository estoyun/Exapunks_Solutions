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
