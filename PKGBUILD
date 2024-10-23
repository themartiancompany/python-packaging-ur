# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

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
_pkg=packaging
pkgname="${_py}-${_pkg}"
pkgver=23.2
pkgrel=1
pkgdesc="Core utilities for Python packages"
arch=(
  'any'
)
_http="https://github.com"
_ns="pypa"
url="${_http}/${_ns}/${_pkg}"
license=('Apache')
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-flit-core"
)
checkdepends=(
  "${_py}-pytest"
  "${_py}-pretend"
)
source=(
  "${url}/archive/$pkgver/$pkgname-$pkgver.tar.gz"
)
sha512sums=(
  '77dfeb0dc6499c55eb5bc4a5bdcdaa146122b97e8f6190c0bf75baadb4e89e4cb5b62ac7d96175acc3d8b387507472b97f0bf18c70df2b6aa78ac54e6c0eb5a3'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    -nw
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
  PYTHONPATH=src \
  pytest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
}
