# bup-pkgbuild-msys

PKGBUILD file for msys pacman

## **winsymlinks:nativestrict feature is required**

In `msys2_shell.cmd`:

`set MSYS=winsymlinks:nativestrict`
<https://www.cygwin.com/cygwin-ug-net/using-cygwinenv.html>

## scoop shim

Create `scoop.sh` at /etc/profile.d

```bash
export PATH=$PATH:/c/users/user_name/scoop/shims
# replace user_name with your user or use your scoop shims path
```

`scoop install pandoc`  
`scoop install git` (optional, git in msys shold also work)

## build depencies

`make gcc python3 rsync`
