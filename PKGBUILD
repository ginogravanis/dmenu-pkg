#!/usr/bin/env bash
# Maintainer: Gino Gravanis

pkgname=dmenu
pkgver=5.2.14.gd584fa0
pkgrel=1
pkgdesc='Dynamic menu for X'
arch=('i686' 'x86_64')
url='https://tools.suckless.org/dmenu/'
license=('MIT')
depends=('libxft' 'libxinerama')
makedepends=('git')
source=('git+https://github.com/ginogravanis/dmenu.git')
md5sums=(
   'SKIP'
)

pkgver() {
   git -C "$srcdir/$pkgname" describe --long --tags | sed 's/-/./g'
}

build() {
   make -C "$srcdir/$pkgname"
}

package() {
   local srcroot="$srcdir/$pkgname"
   make -C "$srcdir/$pkgname" PREFIX=/usr DESTDIR="$pkgdir/" install
   install -Dm644 "$srcroot/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
   install -Dm644 "$srcroot/README.md" "$pkgdir/usr/share/doc/$pkgname/README.md"
}
