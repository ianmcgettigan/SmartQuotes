# SmartQuotes
Turn all instances of "some text" into properly formatted LaTeX ``some text'' 

Add this to your `vimrc` (vim, :edit $MYVIMRC):

```vimscript
" Replace all smart quotes with LaTeX-formatted quotes
" initialize a global toggle
let g:quote_open = 1

" function to return `` or '' alternately
function! SmartQuotes() abort
  if g:quote_open
    let g:quote_open = 0
    return '``'
  else
    let g:quote_open = 1
    return "''"
  endif
endfunction

" command to fix all quotes in the buffer
command! FixQuotes let g:quote_open = 1 | %s/"/\=SmartQuotes()/g
```

**How to use**

Go to your `.tex` file with the incorrect quotes, and run `:FixQuotes`. That's it.
