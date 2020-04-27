### try with CTF-y type things, or if you dgaf and want to be noisy.

wfuzz -w /usr/share/wordlists/wfuzz/general/http_methods.txt -w /usr/share/wordlists/wfuzz/general/common.txt -w /usr/share/wordlists/wfuzz/general/extensions_common.txt -X FUZZ --hc 501,405,404 http://some.webapp:PORT/FUZ2ZFUZ3Z
