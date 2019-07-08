#diff a file hash with its published value
`diff <(shasum -a 256 /path/to/file.ext) <(echo "published_sha256_value")`

