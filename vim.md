## VIM: Useful cmds/tricks

### Replace newline with whatever in Command Mode

`.,$-1s/\n/<whatever>/g`

`.,$-1` == basically means "start at the beginning (.) and replace up to the second to last ($-1)". You might not need to replace the very last newline. Use

`s/\n/<whatever>/g`

to replace everything. Be sure to type `gg` to get to the beginning of the file prior to running these cmds.
