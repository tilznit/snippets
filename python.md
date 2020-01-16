# python
### change a string to a list of integers of _n_ length


```python
m ='some_string' # was an int
n = 0 # enter an integer
new_list = [int(m[i:i+n]) for i in range (0,len(m),n)]

# Useful for iterating over a str that was an int. Weird things happen if len(m) mod n != 0.

```
### diff-ing tool. nice for stuff like .jpgs

```python
a = open("filename", "r").read()
b = open("filename", "r").read()

x = y = []

for i,j in zip(a, b):
    if i != j:
        x.append(i)
        #y.append(j)
        
print x[::2]```
