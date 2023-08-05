# modify based on
# https://gitlab.archlinux.org/archlinux/packaging/packages/bup/-/blob/main/PKGBUILD
pkgname="bup"
pkgver="0.34"
pkgrel=1
pkgdesc='Efficient backup system based on the git packfile format'
arch=("x86_64")
url='https://bup.github.io/'
license=(GPL)
depends=('python>=3.7','gettext-devel','rsync')
optdepends=('libreadline-devel','pandoc')
makedepends=('gcc>=4','make')
license=('LGPL2')

prepare() {
    cd "$srcdir/$pkgname-$pkgver"
}
build() {
    cd "$srcdir/$pkgname-$pkgver"
    ./configure
    make
    find -name '*.so' | while read line; do mv $line ${line/.so/.dll}; done
}
package() {
    cd "$srcdir/$pkgname-$pkgver"
    make DESTDIR="$pkgdir" PREFIX=/usr install
    # msys special
    # find $pkgdir/usr/bin -name 'bup*' | while read line; do rm -f $line; done

    DUMMY_BUP='/usr/lib/bup/cmd/bup.exe'
    DUMMY_BUP_DIR=$(dirname $DUMMY_BUP)
    if [ -f '/usr/lib/bup/cmd/bup.exe' ]; then
        DUMMY_BUP=false
    else
        if ! [ -d $DUMMY_BUP_DIR ]; then
            DUMMY_BUP_DIR=true
            mkdir -p $DUMMY_BUP_DIR
        fi
    fi
    ln -sfr -t $pkgdir/usr/bin '/usr/lib/bup/cmd/bup.exe' bup
    find $pkgdir/usr/lib/bup -name '*.so' | while read line; do mv $line ${line/.so/.dll}; done

    if $DUMMY_BUP; then rm /usr/lib/bup/cmd/bup.exe; fi
    if $DUMMY_BUP_DIR; then rmdir /usr/lib/bup/cmd; fi
    unset DUMMY_BUP DUMMY_BUP_DIR
}
install=bup.install
