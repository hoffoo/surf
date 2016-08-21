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
        'change_clipboard.diff'
        'homepage_on_blank_url.diff'
        )
md5sums=('SKIP'
         'SKIP'
         '8fd342cae180ba787248fbf54da52529'
         'a50bd6b6adedbed8f7e3c60bde417af4'
         'd4bc778f46104177963af2f04e903f47'
         )

pkgver() {
  cd "$_pkgname"
  git describe --tags | sed 's/-/\./g'
}

prepare() {
  cd "$_pkgname"
  patch -i $srcdir/surf-0.6-homepage.diff
  patch -i $srcdir/change_clipboard.diff surf.c
  patch -i $srcdir/homepage_on_blank_url.diff surf.c
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
