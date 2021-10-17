# Changeing a readonly file with vi
There seems to be some different approachs, depending on your current problem:

1. **Readonly** by vi. If your file has ```:set readonly``` you can
    * Use ```:w!``` to force write, or
    * Issue ```:set``` noreadonly and then just use normal ```:w```
2. A permission problem (**sudo**): you can't write but you have sudo rights.
    * Issue: ```:w !sudo tee %```. This will write the buffer to tee, a command that receives pipe information and can write to files. And as tee is run with sudo powers, tee can modify the file.
3. A **permission** problem (**no sudo**): you don't have rights to write the file and you don't have admin access.
    * Use ```:w! ~/tempfile.ext``` to write your changes to a temporary file and then take measures to move the temp file to the directory (send the temp file to the directory owner/admin).

## Shortcut

As it is often the case problem #2 (**permission** problem, with **sudo**), you can to your ```/etc/vim/vimrc``` (or ```~/.vimrc```) the following shortcut:

```cnoremap w!! execute 'silent! write !sudo tee % >/dev/null' <bar> edit```!

Then you can just type ```:w!!``` to save with **sudo** powers. I won't explain it here but the references above cover many shortcuts.

## Thanks: 
* [DrBeco](https://superuser.com/users/93204/drbeco) for your [answer](https://superuser.com/a/785016)

