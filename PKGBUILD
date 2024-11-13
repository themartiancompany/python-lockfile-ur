# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=lockfile
_Pkg="py${_pkg}"
pkgbase="${_py}-${_pkg}"
pkgname=(
  "${_py}-${_pkg}"
)
pkgver=0.12.2
pkgrel=13
pkgdesc='Platform-independent file locking module'
arch=(
  any
)
_http="https://github.com"
_ns="openstack"
url="${_http}/${_ns}/${_Pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
)
makedepends=(
  "${_py}-setuptools"
  "${_py}-pbr"
)
checkdepends=(
  "${_py}-nose"
)
_pypa="https://files.pythonhosted.org/packages/source"
source=(
  "${_pypa}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
)
sha256sums=(
  '6aed02de03cba24efabcd600b30540140634fc06cfa603822d508d5361e9f799'
)

build() {
  ls
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  ls
  "${_py}" \
    "setup.py" \
      build
}

check() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  nosetests
}

package() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \ 
    setup.py \
      install \
        --root="${pkgdir}" \
	--optimize=1
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
