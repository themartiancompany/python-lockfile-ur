
pkgbase=python-lockfile
pkgname=(python-lockfile python2-lockfile)
pkgver=0.12.2
pkgrel=3
pkgdesc='Platform-independent file locking module'
arch=(any)
url='https://github.com/openstack/pylockfile'
license=(MIT)
makedepends=(python-setuptools python2-setuptools)
checkdepends=(python-jinja python2-jinja python-nose python2-nose python-docutils python2-docutils) # tests need older version of python-sphinx
source=(https://pypi.python.org/packages/source/l/lockfile/lockfile-$pkgver.tar.gz)
sha1sums=('c2ac46e48585e5f8f8d57ccc55ca83faa8b53b86')

prepare() {
  cp -a lockfile-$pkgver{,-py2}
}

build() {
  cd "$srcdir/lockfile-$pkgver"
  python setup.py build

  cd "$srcdir/lockfile-$pkgver-py2"
  python2 setup.py build
}

check() {
  cd "$srcdir/lockfile-$pkgver"
  python setup.py test

  cd "$srcdir/lockfile-$pkgver-py2"
  python2 setup.py test
}

package_python-lockfile() {
  depends=(python)

  cd "$srcdir/lockfile-$pkgver"
  python setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

package_python2-lockfile() {
  depends=(python2)

  cd "$srcdir/lockfile-$pkgver-py2"
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
