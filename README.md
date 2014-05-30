prism-powershell
================

Two simple javascript syntax files to support basic Windows PowerShell syntax highlighting on [prism.js](http://prismjs.com) supported systems.

## Installation: Ghostium
Follow the steps in [this blog](http://pantleg.net/2014/05/04/i-did-something/). Once the `./ghostium/src/assets/_components/prism/components` directory exists, copy the two .js files into that directory. Follow the remainder of the steps, including editing the `src/default.hbs` config file and rebuilding Ghostium. Note that prior to the final rebuild, you should make backups of your `config.hbs` and `navigation.hbs` files - restoring them after the rebuild.

Note that I opted not to define custom tokens for psactions/psvars. In doing so, it removes the requirement to add new entries to whatever Prism theme is currently in use. I chose pre-existing tokens that work pretty well with the okaidia theme, your mileage may vary with custom themes/other Prism themes.

## Known issues
This is a first attempt at adding syntax highlighting for a complex language. As a result, there are a few known issues:

* Nested tokens (e.g. strings containing variables) follow the outermost highlighting rule.
* May cause weird color selection in non-okaidia Prism themes.

## Misc

More information and examples can be found on my ghost blog post [here](http://blog.briankmarsh.com/prismjs-powershell-syntax-highlighting/).
