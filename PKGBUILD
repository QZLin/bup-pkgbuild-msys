# modify based on
# https://gitlab.archlinux.org/archlinux/packaging/packages/bup/-/blob/main/PKGBUILD
pkgname="bup"
pkgver="0.34"
pkgrel=1
pkgdesc='Efficient backup system based on the git packfile format'
arch=("x86_64")
url='https://bup.github.io/'
license=(GPL)
depends=('python>=3.7','gettext-devel','rsync','git')
optdepends=('libreadline-devel','pandoc')
makedepends=('gcc>=4','make')

ln_fixed() {
    rm -f $1
    touch $1
    ln -srf $1 $2
    rm -f $1
}
build() {
    cd "$srcdir/$pkgname-$pkgver"
    ./configure
    ln_fixed lib/cmd/bup.exe bup

    pushd 'lib/bup'
    ln_fixed _helpers.so _helpers.dll
    popd
    make
    # find -name '*.so' | while read line; do mv $line ${line/.so/.dll}; done
}
package() {
    cd "$srcdir/$pkgname-$pkgver"
    make DESTDIR="$pkgdir" PREFIX=/usr install
    rm -f "$pkgdir/usr/bin/bup"
    touch "$pkgdir/usr/bin/bup"
    rm -f "$pkgdir/usr/lib/bup/bup/_helpers.dll"
    touch "$pkgdir/usr/lib/bup/bup/_helpers.dll"
}
install=bup.install
