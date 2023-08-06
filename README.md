# bup-pkgbuild-msys

## **winsymlinks:nativestrict feature is required**

> msys2_shell.cmd

`set MSYS=winsymlinks:nativestrict`

## scoop shim

Create `scoop.sh` at /etc/profile.d

```bash
export PATH=$PATH:/c/users/user_name/scoop/shims
# or your scoop shims path
```

`scoop install pandoc`  
`scoop install git` (optional, git in msys shold also work)

## depencies

`make`
