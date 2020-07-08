# GOAL
~~~
File 200 contains exactly one number, N.
Create a new file in t he outbox containing the numbers N through 0 in decreasing order.
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