# emacs

## opening files with `sudo`

When you open a file, if you start the path with `/sudo:root@localhost:` you'll get a prompt for your user's `sudo` password. After entering a correct password, you enter the file path.

So `/sudo:root@localhost:/some/protected/file` is a more convenient way to edit the file, rather than quitting and running `sudo emacs /some/protected/file`.

### bookmarking with `sudo`

You can also use `/sudo:` in bookmarks. I've got a bookmark called "hosts" which jumps to `/sudo:root@localhost:/etc/hosts`
