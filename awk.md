# AWK tricks

### Define an input field separator

example: extract the text from a specific html tag.

`curl http://some.web.site | awk -F \> '{print$5}' | ...`

uses each > in a html tag as a separator. If you needed to get to a specific `<h3>` tag at the position `$5`, the info for `'{print$5}'` would return

`blah blah blah</h3`

use something like

`sed 's/...$//` to nix the trailing chars and return `blah blah blah` and pass it into a variable, or whatever you need to do with the info.

also handy for quicly getting port numbers from nmap output:

```bash
cat alltcp.nmap | grep open | awk -F/ '{print$1}' ORS=','

21,22,80,
```

### Insert a string every N rows in a file

```bash
awk ' {print;} NR % 2 == 0 { print "sometext"; }' inputfile

# inputfile is file with lines you want to insert "sometext" into

line1
line2
sometext
line3
line4
sometext
...
```
