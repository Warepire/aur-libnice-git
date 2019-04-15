# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: William Díaz <wdiaz@archlinux.us>

_pkgname=libnice
pkgname=$_pkgname-git
pkgver=0.1.15+47+g62cbfbd
pkgrel=1
pkgdesc="An implementation of the IETF's draft ICE (for p2p UDP data streams)"
url="https://nice.freedesktop.org"
arch=(x86_64)
license=(LGPLv2.1)
depends=(glib2 gnutls gupnp-igd)
makedepends=(gstreamer gtk-doc git meson gobject-introspection)
optdepends=(gstreamer)
provides=(libnice)
conflicts=(libnice)
source=('git+https://gitlab.freedesktop.org/libnice/libnice.git')
sha256sums=('SKIP')

pkgver() {
  cd $_pkgname
  git describe --tags | sed 's/-/+/g'
}

prepare() {
  cd $_pkgname
}

build() {
  arch-meson $_pkgname build -D gtk_doc=enabled -D tests=disabled -D introspection=disabled
  ninja -C build
}

check() {
  meson test -C build --print-errorlogs
}

package() {
  DESTDIR="$pkgdir" meson install -C build
}
