# Maintainer: megadriver <megadriver at gmx dot com>

pkgname=firefox-beta-bin-es-es
pkgver=14.0b8
pkgrel=1
pkgdesc="Standalone web browser from mozilla.org (Beta channel, Castilian Spanish)"
url="http://www.mozilla.org/es-ES/firefox/channel/"
arch=('i686' 'x86_64')
license=('MPL' 'GPL2' 'LGPL2')
depends=('sqlite3' 'nss' 'libxt' 'gtk2' 'desktop-file-utils' 'alsa-lib' 'dbus-glib')
install=$pkgname.install
source=(ftp://ftp.mozilla.org/pub/firefox/releases/${pkgver}/linux-${CARCH}/es-ES/firefox-${pkgver}.tar.bz2
        firefox-beta.desktop firefox-beta-safe.desktop)
md5sums=('6f9e591c0e960f48dd3723f678ef1330'
         'f66d831fcf7a6a60be44a78e44a34fb0'
         '1f947ba2b9ec501268cd5bdf9e20e540')

[[ "$CARCH" == "x86_64" ]] && md5sums[0]="1a3d244955effa9545c2f175dd075ed5"

build() {
  install -d $pkgdir/usr/lib/$pkgname $pkgdir/usr/bin/
  cp -a $srcdir/firefox/* $pkgdir/usr/lib/$pkgname/

  # Comment out the following line if you want the Feedback extension
  rm -rf $pkgdir/usr/lib/$pkgname/distribution

  # Comment out the following line if you want to activate the Crash Reporter
  sed -i 's/Enabled=1/Enabled=0/g' $pkgdir/usr/lib/$pkgname/application.ini

  ln -s /usr/lib/$pkgname/firefox $pkgdir/usr/bin/firefox-beta

  install -d $pkgdir/usr/share/applications/ $pkgdir/usr/share/pixmaps/
  install -m644 $srcdir/firefox-beta.desktop $pkgdir/usr/share/applications/
  install -m644 $srcdir/firefox-beta-safe.desktop $pkgdir/usr/share/applications/
  install -m644 $srcdir/firefox/icons/mozicon128.png $pkgdir/usr/share/pixmaps/firefox-beta.png
}
