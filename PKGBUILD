pkgname=reaver-wps-fork-t6x-git
_pkgname=reaver-wps-fork-t6x
pkgver=1.5.2.r9.g6e60ee2
pkgrel=1
pkgdesc="Brute force attack against Wifi Protected Setup mod with Pixie Dust Attack"
arch=('arm' 'armv6h' 'armv7h' 'i686' 'x86_64')
url="https://github.com/t6x/reaver-wps-fork-t6x"
license=('GPL2')
depends=('libpcap' 'sqlite3' 'pixiewps')
makedepends=('git')
backup=('etc/reaver/reaver.db')
replaces=('reaver' 'reaver-svn' 'reaver-git' 'reaver-wps-fork-t6x')
conflicts=('reaver' 'reaver-svn' 'reaver-git' 'reaver-wps-fork-t6x')
provides=('reaver')
source=("$pkgname::git+https://github.com/t6x/$_pkgname.git")
sha256sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd "$pkgname/src"
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  cd "$pkgname"
  install -Dm755 src/reaver "$pkgdir/usr/bin/reaver"
  install -Dm755 src/wash "$pkgdir/usr/bin/wash"
  install -Dm644 src/reaver.db "$pkgdir/etc/reaver/reaver.db"
  install -Dm644 docs/README "$pkgdir/usr/share/doc/reaver/README"
  install -Dm644 docs/reaver.1.gz "$pkgdir/usr/share/man/man1/reaver.1.gz"
}
