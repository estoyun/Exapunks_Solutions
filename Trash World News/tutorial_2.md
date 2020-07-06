# GOAL
~~~
1. Append the correct value to the end of file 200.
2. Move file 200 to the outbox.  
3. Leave no trace.
~~~

# CONDITION
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
