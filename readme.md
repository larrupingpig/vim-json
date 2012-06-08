VIM JSON
========

Customization on Jeroen Ruigrok van der Werven's [vim-json highlighting script](http://www.vim.org/scripts/script.php?script_id=1945)
[Pathogen-friendly.](https://github.com/tpope/vim-pathogen)

Specific modifications:
-----------------------

Added the filetype `.json.js` to autodetection.
Added syntax highlighting warning for decimals smaller than 1 that don't start with a 0 (so .1 gives a warning, it should be 0.1).
Added syntax highlighting warning for comments and semicolons.
Added distinct highlighting for keywords.


Why use separate JSON highlighting instead of just Javascript?
--------------------------------------------------------------

Here's 2 compelling reasons:

1. **All JSON is Javascript but NOT all Javascript is JSON.** So `{property:1}` is invalid because `property` does not have double quotes around it. `{'property':1}` is also invalid, because it's single quoted while the only thing that can placate JSON is double quoting. JSON is even fuzzy enough that `{"property":.1}` is invalid, because you should have of course written `{"property":0.1}`. Also, don't even think about having comments or semicolons, you guessed it: they're invalid. The point being that your syntax highlighter should warn you about these errors, in realtime, which is something that the Javascript highlighter doesn't (because in Javacript they're not errors!).

2. **Distinct highlighting for keywords.** JSON is an extremely lightweight data format but at it's core lies an inescapable conceptual distinction: there are keywords and then there are values. There's nothing much to the format besides that, so we might as well display keywords and values differently. This is something that gets lost with Javascript-inspired syntax highlighters, which see keywords as just another string since JSON requires them double quoted.
