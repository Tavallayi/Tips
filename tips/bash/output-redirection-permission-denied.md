When root is the owner of the directory where you want to create `hello` file and users from the same group and other users doesn't have permission to write in that directory, you will get `-bash: hello: permission denied` error when you run `ls -laR > hello`.

Moreover, you will get exactly the same error when you run the same command using `sudo` in front of it. This because output redirection (the `>` operator) is done by the shell, not by `ls`, so sudo has no effect upon it. `sudo` has effect only on `ls  -laR`. To prevent this, you have to login as root:
```sh
sudo -i
```
Then you can use redirection:
```sh
ls -laR > hello
```
Otherwise, you can run your bash command in a subshell with root privileges:

```sh
sudo bash -c "ls -laR > hello"
```
Finally, another option, instead to use redirection via the > operator, you can use tee command:

```sh
ls -laR | sudo tee hello
```
You don't have to use in this case sudo for ls command because users from the same group with root and all other users have read and execution permission in that directory.

# Thanks: 
* [Radu Rădeanu](https://askubuntu.com/users/147044/radu-r%c4%83deanu) for your [answer](https://askubuntu.com/a/382546)