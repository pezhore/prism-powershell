prism-powershell
================

Two simple Javascript syntax files to support basic Windows PowerShell syntax highlighting on [prism.js](http://prismjs.com) supported systems.

## About
Based loosely on the existing clike language definition, with several changes:

* Updated the comment token's regex to accommodate multi-line comments (`<# whatever #>`), and single line comments (`# this is a comment`).
* Updated the string token's regex to accommodate multi-line string (`@" ... "@`).
* Updated the keyword token's regex to add PowerShell specific keywords (switch, begin, process, end).
* Updated the boolean token's regex to include the leading `$`.
* Added the attr-value token with regex to match PowerShell Actions (based on the [approved PowerShell verbs](http://msdn.microsoft.com/en-us/library/ms714428%28v=vs.85%29.aspx)).
* Added the symbol token with regex to match PowerShell variables (other than `$true | $false`).
* Updated the operator token's regex to include the various PowerShell comparison operators (-or, -le, etc)

## Installation: Ghostium
Follow the steps in [this blog](http://pantleg.net/2014/05/04/i-did-something/). Once the `./ghostium/src/assets/_components/prism/components` directory exists, copy the two .js files into that directory. Follow the remainder of the steps, including editing the `src/default.hbs` config file and rebuilding Ghostium. Note that prior to the final rebuild, you should make backups of your `config.hbs` and `navigation.hbs` files - restoring them after the rebuild.

Note that I opted not to define custom tokens for psactions/psvars. In doing so, it removes the requirement to add new entries to whatever Prism theme is currently in use. I chose pre-existing tokens that work pretty well with the okaidia theme, your mileage may vary with custom themes/other Prism themes.

## Known issues
This is a first attempt at adding syntax highlighting for a complex language. As a result, there are a few known issues:

* Nested tokens (e.g. strings containing variables) follow the outermost highlighting rule.
* May cause weird color selection in non-okaidia Prism themes.
* Some code in prism.js replaces "`<`" with "`&lt;`" behind the scenes and breaks what would normally be expected for PowerShell block comments: `/<#[\w\W]*?#>/g`. I had to change the regex to accommodate this substitution (`/\&lt;#[\w\W]*?#>/g`).

## Misc

More information and examples can be found on my ghost blog post [here](http://blog.briankmarsh.com/prismjs-powershell-syntax-highlighting/).
