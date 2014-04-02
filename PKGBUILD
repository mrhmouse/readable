# Maintainer: Jordan Brown <mrhmouse@gmail.com>
pkgname=readable-git
pkgver=20140402
pkgrel=1
pkgdesc="Readable s-expressions for Lisp and Scheme (t-expressions)."
arch=('i686' 'x86_64')
url="http://sourceforge.net/projects/readable/"
license=('MIT')
depends=()
makedepends=('git' 'python' 'autoconf' 'automake' 'guile')
conflicts=()

_gitroot='git://git.code.sf.net/p/readable/code'
_gitname='readable'

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  #
  # BUILD HERE
  #
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_gitname-build"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
