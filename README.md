# ime.gvim - GVim Input Method Optimization Plugin

When using input methods in Vim, it's common to encounter inconvenient mode
switching. This plugin intelligently manages input method states to provide
a smooth input experience.

## Dependencies

> [!WARNING]
> This configuration depends on the effectiveness of the `imdisable` option.
> Please ensure your GVim supports this feature.

## Installation and Configuration

Add the following configuration to your `gvimrc` file:

```Vim
noremap ? <Cmd>set noimdisable<CR>?
noremap / <Cmd>set noimdisable<CR>/
noremap : <Cmd>set noimdisable<CR>:<Del>:
cnoremap <C-C> <Cmd>set imdisable<CR><CR>
cnoremap <CR> <Cmd>set imdisable<CR><CR>
cnoremap <C-[> <Cmd>set imdisable<CR><CR>
augroup IME
    au!
    au GUIEnter * set imdisable           " Disable input method at startup
    au InsertEnter * set noimdisable      " Enable when entering insert mode
    au InsertLeavePre * set imdisable     " Disable when leaving insert mode
augroup END
```

This will achieve an input-method-free environment in normal mode.

## Contribution

As my ability is limited, if you have better suggestions, welcome to submit an
Issue or PR!

## License

MIT © mao-yining
