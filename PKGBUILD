# Maintainer: Limao Luo <luolimao+AUR@gmail.com>
# Contributor: josephgbr <rafael.f.f1@gmail.com>
#
# (Added from ibus package)
# Contributor: Rainy <rainylau@gmail.com>
# Contributor: Lee.MaRS <leemars@gmail.com>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>
# Contributor: Brad Fanella <bradfanella@archlinux.us>

_pkgname=ibus
pkgname=lib32-$_pkgname
pkgver=1.5.1
pkgrel=1
pkgdesc="Next Generation Input Bus for Linux (32-bit libraries)"
arch=(x86_64)
url=http://ibus.googlecode.com
license=(LGPL2.1)
depends=($_pkgname lib32-gtk{2,3})
makedepends=(gcc-multilib gobject-introspection intltool iso-codes lib32-dconf python2-gobject python2-xdg)
options=(!emptydirs !libtool)
install=$_pkgname.install
source=($url/files/$_pkgname-$pkgver.tar.gz)
sha256sums=('6023809ced2794b75fad07eb1b1d6288154b373920ecdcd51582a4cde4e0d017')
sha512sums=('8fcc0a6156d8638023f8a430385abd5a278af1c6fec9127c721831d408157fe5c74a7f2a9a46749d71edd3ea419335f9edce8f095a1414707197c652bdad4404')

build() {
    export PYTHON=python2
    export CC='gcc -m32'
    export PKG_CONFIG_PATH='/usr/lib32/pkgconfig'

    cd $_pkgname-$pkgver/
    ./configure \
        --prefix=/usr \
        --libdir=/usr/lib32 \
        --libexecdir=/usr/lib32/$_pkgname \
        --sysconfdir=/etc \
        --disable-gconf \
        --enable-dconf \
        --disable-memconf \
        --enable-ui \
        --disable-nls
    make
}

package() {
    make -C $_pkgname-$pkgver DESTDIR="$pkgdir" install
    rm -rf "$pkgdir"/{etc,usr/{bin,include,lib,lib32/ibus,share}}
}
