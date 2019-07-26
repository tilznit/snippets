# bash

### diff a file hash with its published value

`diff <(shasum -a 256 /path/to/file.ext) <(echo "published_sha256_value")`

use something like `... | sed 's/ .*$//'` to strip the extraneous info from the shasum cmd. Add info to the end of the published value to test.

`diff <(shasum -a 256 /path/to/file.ext | sed 's/ .*$//') <(echo "published_sha256_value")`

### carve a range of files by exact beginning and end

`ls -lh | grep "some_logs.log" | grep -E "1[3-9].gz|2[0-6].gz"`

Lists only `some_logs_13.gz` to `some_logs_26.gz`. Pipe that into whatever to do whatever.

### find hashes from output

`grep -a [a-z0-9]\{32\}`

Pipe output from things like `strings` here to finds hashes. The above will work for all hashes that are 32 characters or greater (md5, sha256, etc). Not perfect; will catch any string of lowercase letters and/or numbers greater than 32 characters. Adapt as needed. To find sha256 you could do

`grep -a [a-z0-9]\{64\}`
