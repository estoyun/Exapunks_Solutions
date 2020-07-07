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
