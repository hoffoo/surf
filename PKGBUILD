# Maintainer: sekret
_pkgname=surf
pkgname=$_pkgname-git
pkgver=0.7.11.g6c8da4c
pkgrel=1
pkgdesc="a WebKit based browser"
arch=('i686' 'x86_64')
url="http://surf.suckless.org/"
license=('custom:MIT/X')
depends=('webkitgtk2' 'xorg-xprop')
makedepends=('git')
optdepends=('dmenu: url bar and search'
'ca-certificates: SSL verification'
'st: default terminal for the download handler'
'curl: default download handler')
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("$_pkgname::git+http://git.suckless.org/surf"
        'config.h'
        'http://surf.suckless.org/patches/surf-0.6-homepage.diff'
        )
md5sums=('SKIP'
         'SKIP'
         '8fd342cae180ba787248fbf54da52529'
         )

pkgver() {
  cd "$_pkgname"
  git describe --tags | sed 's/-/\./g'
}

prepare() {
  cd "$_pkgname"
}

build() {
  cd "$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir"
}

package() {
  cd "$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
