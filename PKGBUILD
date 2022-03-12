# Maintainer: Gino Gravanis

pkgname=dmenu
pkgver=1
pkgrel=1
pkgdesc='Dynamic menu for X'
arch=('i686' 'x86_64')
url='https://tools.suckless.org/dmenu/'
license=('MIT')
depends=('sh' 'glibc' 'coreutils' 'libx11' 'libxinerama' 'libxft' 'freetype2' 'fontconfig')
makedepends=('git')
provides=()
conflicts=()
source=(
   'git+https://git.suckless.org/dmenu'
   'https://tools.suckless.org/dmenu/patches/border/dmenu-border-4.9.diff'
)
md5sums=(
   'SKIP'
   '4012371a7a77354f4111121ca19c8cd1'
)

prepare() {
   local srcroot="$srcdir/$pkgname"
   for patch in "${source[@]:1}"; do
      patch -d "$srcroot" -p1 -i "$BUILDDIR/$(basename $patch)"
   done
   cp "$BUILDDIR/config.h" "$srcroot/"
   cp "$srcroot/config.def.h" "$BUILDDIR/"
}

pkgver() {
   git -C "$srcdir/$pkgname" describe --long --tags | sed 's/-/./g'
}

build() {
   make -C "$srcdir/$pkgname"
}

package() {
   local srcroot="$srcdir/$pkgname"
   local license_dir="$pkgdir/usr/share/licenses/$pkgname"
   make -C "$srcdir/$pkgname" PREFIX=/usr DESTDIR="$pkgdir/" install
   install -Dm644 "$srcroot/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
   install -Dm644 "$srcroot/README" "$pkgdir/usr/share/doc/$pkgname/README"
}
