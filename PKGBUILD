# Maintainer: Daniel Seymour <dannyseeless at gmail dot com>

pkgname=mediabrowser-server
pkgver=3.0.5621.4
pkgrel=1
pkgdesc="MediaBrowser Server is a home media server built using other popular open source technologies."
arch=('i686' 'x86_64' 'armv6h')
url="http://www.mediabrowser.tv"
license=('GPL')
groups=()
depends=('mono' 'libgdiplus' 'libmediainfo' 'libwebp' 'sqlite' 'ffmpeg')
optdepends=()
conflicts=('mediabrowser-server')
install=mediabrowser-server.install
source=("https://www.github.com/MediaBrowser/MediaBrowser/archive/${pkgver}.tar.gz"
        "mediabrowser-server.service" "mediabrowser-server" "mediabrowser-server.conf")
md5sums=('379d3d1624535c85160f2bc281c6d92f'
         '94940241dbce0ac324b58b673c2cef82'
         'b5fe247b5538bb4fb49bec251b5aac13'
         '0b889497952c8339a3764ed7137dcdf7')

package() {
  mkdir -p ${pkgdir}/usr/lib/mediabrowser-server
  cd ${srcdir}/MediaBrowser-${pkgver}
  xbuild /p:Configuration="Release Mono" /p:Platform="Any CPU" /t:build MediaBrowser.Mono.sln
  cp -r ${srcdir}/MediaBrowser-${pkgver}/MediaBrowser.Server.Mono/bin/Release\ Mono/* ${pkgdir}/usr/lib/mediabrowser-server
  install -Dm644 ${srcdir}/mediabrowser-server.conf ${pkgdir}/etc/conf.d/mediabrowser-server.conf
  install -Dm755 ${srcdir}/mediabrowser-server ${pkgdir}/usr/bin/mediabrowser-server
  install -Dm644 ${srcdir}/mediabrowser-server.service ${pkgdir}/usr/lib/systemd/system/mediabrowser-server.service
}
