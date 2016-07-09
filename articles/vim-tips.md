## VIM Tips
<!-- toc -->

### 快速插入当前时间到文本中
来源[best way to insert timestamp in vim](http://stackoverflow.com/questions/56052/best-way-to-insert-timestamp-in-vim/58604#58604)
```bash
nmap <F3> i<C-R>=strftime("%Y-%m-%d %a %I:%M %p")<CR><Esc>
imap <F3> <C-R>=strftime("%Y-%m-%d %a %I:%M %p")<CR>
```
