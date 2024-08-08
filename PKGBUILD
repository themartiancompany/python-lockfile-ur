# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

pkgbase=python-lockfile
pkgname=(python-lockfile)
pkgver=0.12.2
pkgrel=13
pkgdesc='Platform-independent file locking module'
arch=(any)
url='https://github.com/openstack/pylockfile'
license=(MIT)
depends=(python)
makedepends=(python-setuptools python-pbr)
checkdepends=(python-nose)
source=(https://files.pythonhosted.org/packages/source/l/lockfile/lockfile-$pkgver.tar.gz)
sha256sums=('6aed02de03cba24efabcd600b30540140634fc06cfa603822d508d5361e9f799')

build() {
  cd "$srcdir/lockfile-$pkgver"
  python setup.py build
}

check() {
  cd "$srcdir/lockfile-$pkgver"
  nosetests
}

package() {
  cd "$srcdir/lockfile-$pkgver"
  python setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
