# GOAL
~~~
1. Move file 200 to the outbox.  
2. Leave no trace.
~~~

# CONDITION
~~~
200 "MOVE, THIS, FILE, TO, THE, OUTBOX"
~~~

# SOLUTION
~~~
LINK 800  
GRAB 200  
LINK 800  
DROP  
HALT
~~~
