# Maintainer: Padfoot

pkgname=lightdm-gtk-greeter-no-gnome
srcname=lightdm-gtk-greeter
pkgver=1.1.5
pkgrel=1
pkgdesc="GTK+ greeter for LightDM without gnome dependencies"
arch=('i686' 'x86_64')
license=('GPL3' 'LGPL3')

url="https://launchpad.net/lightdm-gtk-greeter"
source=("https://launchpad.net/$srcname/trunk/$pkgver/+download/$srcname-$pkgver.tar.gz"
lightdm-gtk-greeter.conf)
depends=('lightdm=>1.2.0' 'gtk3')
makedepends=('gtk-doc' 'gnome-common' 'gnome-doc-utils' 'gobject-introspection' 'pkg-config' 'intltool')
optdepends=('xorg-xserver-xephr: run lightdm in test mode')
install=lightdm-gtk-greeter.install

conflicts=('lightdm-gtk-greeter')
provides=('lightdm-gtk-greeter')

backup=('etc/lightdm/lightdm-gtk-greeter.conf')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./autogen.sh --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib/lightdm \
    --disable-static
    
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  
  make DESTDIR="${pkgdir}" install

  cp ../lightdm-gtk-greeter.conf $pkgdir/etc/lightdm
}

md5sums=('e42cedadbebd5b45733b32db54b83a44'
         'd8b7a9bb10dee7597af9e8d310446829')
