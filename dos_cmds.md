### grep-like exclude

`netstat -ano | findstr /v "10.10.14.162"`

### edit text files in the Windows command prompt

`copy con c:\file.txt  
#Then enter the text you want to put in the file.`

### network ping sweep
`for /L %i in (1,1,255) do @ping -n 1 -w 200 172.16.2.%i > nul && echo 172.16.2.%i is up`

### find a file recursively
`dir filename.ext /S /B`

### view contents of a file
```dos
more file.txt
type file.txt
```
