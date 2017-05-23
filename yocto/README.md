# Example
The `yocto` script mounts the current directory and adds a user with the same guid and uuid as the current user, then it starts a bash shell into the docker container.
```bash
starlord@host $ docker build -t yocto .
starlord@host $ alias yocto=$(pwd)/yocto
starlord@host $ yocto bash
yocto@deadbeef $ git clone git://git.yoctoproject.org/poky.git
yocto@deadbeef $ source poky/oe-init-build-env
yocto@deadbeef $ time bitbake core-image-base
```
