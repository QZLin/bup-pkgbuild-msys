# modify based on
# https://gitlab.archlinux.org/archlinux/packaging/packages/bup/-/blob/main/PKGBUILD
pkgname="bup"
pkgver="0.1"
pkgrel=1
pkgdesc='Efficient backup system based on the git packfile format'
arch=("x86_64")
url='https://bup.github.io/'
license=(GPL)
depends=('python>=3.7','gettext-devel','rsync')
optdepends=('libreadline-devel','pandoc')
makedepends=('gcc>=4','make')
license=('LGPL2')

build() {
    cd "$srcdir/$pkgname-$pkgver"
    ./configure --prefix=/usr
    make
}
package() {
    cd "$srcdir/$pkgname-$pkgver"
    make DESTDIR="$pkgdir/" install
    rm $pkgdir/usr/local/bin/bup
}
install=bup.install
