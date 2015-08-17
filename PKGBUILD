# Maintainer: Vasil Yonkov <bustervill at gmail dot com>
pkgname=rbfu-git
pkgver=20120930
pkgrel=1
pkgdesc="Minimal Ruby version management is minimal."
arch=('i686' 'x86_64')
url="https://github.com/hmans/rbfu/"
license=('MIT')
makedepends=('git')
provides=('ruby' 'rubygems' 'rake')
install="rbfu-git.install"

_gitroot="git://github.com/hmans/rbfu.git"
_gitname="rbfu"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server..."
  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone --depth=1 $_gitroot $_gitname
  fi
  msg "GIT checkout done or server timeout"
}

package() {
  cd "$srcdir/$_gitname"
  mkdir -p $pkgdir/usr/bin

  cp bin/rbfu $pkgdir/usr/bin
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et: