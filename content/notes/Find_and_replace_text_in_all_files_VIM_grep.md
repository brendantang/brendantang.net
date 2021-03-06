---
title: "Find and Replace text in all files that contain it using VIM and grep"
date: 2020-10-07T11:59:16-04:00
tags: ['technical notes', 'unix', 'vim', 'grep']
---

I'm no wizard with VIM or `grep`, so it helps me to use this post as a cheatsheet.

If I need to, for example, rename a method everywhere that it occurs in a project, I use these commands:

Recursively list all files in a given directory with matching text, then open them all in vim buffers:[^1]

```
vim `grep -rwl '/path/to/look/in' -e 'string_to_match'`
```

If you want to avoid binary files, also add the -I option. This is useful for me when grepping inside of a rails project's 'db' directory but not wanting to search .sqlite files.

Once VIM is open use `:ls` to list all open buffers, `:b 1` to go to buffer 1, etc.[^2]

Find and replace a phrase across all buffers (with confirmation):

```
:bufdo %s/pattern/replacement/gc
```

Without confirmation:[^3]

```
:budfo %s/pattern/replacement/ge | update
```

[^1]: [Stack overflow answer](https://stackoverflow.com/a/16957078) explaining the `grep` command options
[^2]: [VIM buffers reference](https://vim.fandom.com/wiki/Vim_buffer_FAQ)
[^3]: [Reference](https://vim.fandom.com/wiki/Search_and_replace_in_multiple_buffers) for find and replace across buffers 
