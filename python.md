# python
### change a string to a list of integers of n length


```python
m ='some_string' # was an int
n = '' # an integer
new_list = [int(m[i:i+n]) for i in range (0,len(m),n)]

# useful for iterating over a str that was an int. infinite decsent AES. Wierd things happen if n is not a divisor of len(m).

```