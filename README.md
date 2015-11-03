objc_matchbracket: Insert Matching Start Bracket for Vim
========================================================

`qqshfox` didn't update `objc_matchbracket` for a long time.
So I decide to take it over. 
I have added a few cases to make it closer to what XCode does.

This is essentially TextMate's "Insert Matching Start Bracket" feature implemented in vim script. Makes it a lot more pleasant to write Objective-C.

Just type ] in insert mode after an object or method you want to wrap in brackets and this will wrap it appropriately; to escape out of it once you're finished, simply type ] again.

For instance, where | is the cursor:
```objc
"foo|" becomes "[foo |]" after ] is pressed.
"foo bar|" becomes "[foo bar]|"
"foo: bar|" becomes "foo: [bar |]"
"foo bar: baz|" becomes "[foo bar: baz]|"
"foo bar: self.baz|" becomes "[foo bar: self.baz]|"
"foo bar: self baz|" becomes "foo bar: [self baz]|"
```

Certain useful keywords are also wrapped intelligently, for example:
```objc
"return foo|" becomes "return [foo ]|"
"@selector: foo|" becomes "[@selector: foo]|"
```

Hope you like it!

TODO: [TextMate](https://github.com/textmate/objective-c.tmbundle/blob/master/Commands/Insert%20Matching%20Start%20Bracket.tmCommand) uses stacks to parse the objc code. However, `qqshfox` uses regular expression to deal with it. Regular expression cannot parse the bracket location correctly, so `objc_matchbracket` cannot work 100% correctly. 
