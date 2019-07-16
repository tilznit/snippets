# python
### change a string to a list of integers of _n_ length


```python
m ='some_string' # was an int
n = 0 # enter an integer
new_list = [int(m[i:i+n]) for i in range (0,len(m),n)]

# Useful for iterating over a str that was an int. Weird things happen if n is not a divisor of len(m).

```
