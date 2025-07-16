# Maintainer: Joe User <joe.user@example.com>
pkgname=wlroots0.19-westmere
pkgver=0.19
pkgrel=1
pkgdesc="wlroots with westmere patches"
arch=('x86_64')
url="https://swaywm.org/"
license=('MIT')
depends=('libinput' 'libxkbcommon' 'pixman' 'mesa' 'libdrm' 'wayland')
makedepends=('wayland-protocols' 'wayland' 'vulkan-headers' 'xorg-xwayland')
optdepends=('swaync: simple sway notification demon')
source=("https://github.com/AlieeLinux/wlroots0.19-westmere/releases/download/wl/wlroots-0.19.0.tar.gz")
sha256sums=('aefb0fe2633b0aad1d66123b2f41afab004fb625e2a7790492cdd39a805cac91')
provides=("wlroots0.19")
replaces=("wlroots0.19")
conflicts=('wlroots0.19')

build() {
        export CFLAGS="-march=westmere -mtune=nehalem -O2 -pipe -fstack-protector-strong -fno-plt -fPIC"
        export CXXFLAGS="${CFLAGS}"
        tar -xvf "wlroots-0.19.0.tar.gz" -C "$srcdir"
        cd "$srcdir/wlroots-0.19.0"
        mkdir build
        arch-meson build --prefix=/usr -Dc_args="$CFLAGS" -Dcpp_args="$CFLAGS" 
        ninja -C build -j $(nproc)
}
package() {
        cd "$srcdir/wlroots-0.19.0"
        DESTDIR="$pkgdir/" ninja -C build install -j2
}
