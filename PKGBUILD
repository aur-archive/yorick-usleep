# Maintainer: Francois Rigaut <frigaut at gmail dot com>

pkgname=yorick-usleep
pkgver=20140916
pkgrel=1
pkgdesc="usleep function"
arch=('i686' 'x86_64')
license=('GPL')
url="http://www.maumae.net/yorick/doc/plugins.php"
groups=('science' 'yorick-all')
depends=('yorick')
makedepends=('yorick')

_gitroot="git://github.com/frigaut/yorick-usleep.git"
_gitname="yorick-usleep"

build() {
  cd ${srcdir}
  msg "Connecting to git repo..."
  if [ -d ${srcdir}/$_gitname ] ; then
      cd $_gitname && git pull origin
      msg "The local files are updated."
  else
      git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting script install..."

  git clone $_gitname $_gitname-build
  cd ${srcdir}/$_gitname-build

  yorick -batch make.i
  make
}

package() {
  cd ${srcdir}/$_gitname-build
  make DESTDIR=${pkgdir} install
}
