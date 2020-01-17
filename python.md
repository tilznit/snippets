# python
### change a string to a list of integers of _n_ length


```python
m ='some_string' # was an int
n = 0 # enter an integer
new_list = [int(m[i:i+n]) for i in range (0,len(m),n)]

# Useful for iterating over a str that was an int. Weird things happen if len(m) mod n != 0.

```
### diff tool... nice for diffing files of the same type in ctfs

```python
a = open("filename", "r").read()
b = open("filename", "r").read()

x = ''

for i,j in zip(a, b):
    if i != j:
        #x.append(i) if x needs to be a list
        x += i
        
print x

# Prints a string of differences. Pipe the output into sed to prettify if x is a list. Output may be a flag...

```
