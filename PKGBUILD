_pkgname=win2smb
pkgname=win2smb-git
pkgver=20130110
pkgrel=2
pkgdesc="Convert a Windows style share file path to Samba style."
url="https://github.com/yxd-works/win2smb"
arch=('i686' 'x86_64')
license=('GPLv3')
makedepends=('git' 'ghc' 'cabal-install')
conflicts=('win2smb')
replaces=('win2smb')

_gitroot=git://github.com/yxd-works/win2smb.git
_gitname=${_pkgname}

build() {
  cd ${srcdir}
  msg "Connecting to GIT server...."

  if [[ -d ${_gitname} ]]; then
    cd ${_gitname} && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname" --depth=1
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  cd ${srcdir}/${_gitname}
  cabal configure
  cabal build
}

package() {
  cd ${srcdir}/${_gitname}

  cabal install --ghc -O2 --prefix=${pkgdir}/usr
}
