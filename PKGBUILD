# Maintainer: Alois Nespor <info[at]aloisnespor[dot]info>
# Contributor: archtux <antonio dot arias99999 at gmail dot com>

pkgname=gtksu
pkgver=0.1.1
pkgrel=1
pkgdesc="Simple replacement for gksu/ktsuss etc that allows you to run a program with different privileges (root etc)."
arch=('i686' 'x86_64')
url="http://keithhedger.hostingsiteforfree.com/pages/gtksu/gtksu.html"
license=('GPL3')
depends=('sudo')
optdepends=('gtk2')
provides=('gksu')
conflicts=('gksu')
source=(http://keithhedger.hostingsiteforfree.com/zips/gtksu/GtkSu-$pkgver.tar.gz)
md5sums=('91492228a06c61142bd93cd66b991829')

prepare() {
  cd $srcdir/GtkSu-$pkgver
  ./autogen.sh --prefix=/usr
}

build() {
  cd $srcdir/GtkSu-$pkgver
  make
}

package() {
  cd $srcdir/GtkSu-$pkgver
  make DESTDIR=$pkgdir install

  # Fix desktop file
  cd $pkgdir/usr/share/applications
  sed -i 11,+2d GtkSu.desktop 
  sed -i '10iIcon=/usr/share/GtkSu/pixmaps/GtkSu.png' GtkSu.desktop 
  sed -i '11iExec=gtksu' GtkSu.desktop
  
  #added link as a replacement for gksu
  cd $pkgdir/usr/bin
  ln -s gtksu gksu
  
}
