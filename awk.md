# AWK tricks

### Define an input field separator

example: extract the text from a specific html tag.

`curl http://some.web.site | awk -F \> '{print$5}' | ...`

uses each > in a html tag as a separator. If you needed to get to a specific `<h3>` tag, the info for `'{print$5}'` would return something like

`blah blah blah</h3`

use something like

`sed 's/...$//` to nix the trailing chars and return `blah blah blah`
