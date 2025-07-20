# ime.gvim - GVim 输入法优化插件

在 Vim 中使用输入法时，常遇到模式切换不便的问题。本插件通过智能管理输入法状态，
提供流畅的输入体验。

## 依赖

> [!WARNING]
> 本配置依赖 `imdisable` 选项的有效性，请确保您的 GVim 支持此功能。

## 安装与配置

将以下配置添加到您的 `gvimrc` 文件中：

```Vim
noremap ? <Cmd>set noimdisable<CR>?
noremap / <Cmd>set noimdisable<CR>/
noremap : <Cmd>set noimdisable<CR>:<Del>:
cnoremap <C-C> <Cmd>set imdisable<CR><CR>
cnoremap <CR> <Cmd>set imdisable<CR><CR>
cnoremap <C-[> <Cmd>set imdisable<CR><CR>
augroup IME
    au!
    au GUIEnter * set imdisable           " 启动时禁用输入法
    au InsertEnter * set noimdisable      " 进入插入模式启用
    au InsertLeavePre * set imdisable     " 离开插入模式禁用
augroup END
```

即可实现在 normal 模式下无输入法的干扰。

## 贡献

由于本人的能力有限，如果您有更好的意见，欢迎提交 Issue 或 PR！

## 许可证

MIT © mao-yining
