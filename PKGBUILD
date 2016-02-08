# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-packaging
pkgname=(python-packaging python2-packaging)
_pkgname=packaging
pkgver=16.1
pkgrel=1
pkgdesc="Core utilities for Python packages"
arch=('any')
url="https://github.com/pypa/packaging"
license=('Apache')
makedepends=('python-setuptools' 'python2-setuptools' 'python-pyparsing' 'python2-pyparsing' 'git')
checkdepends=('python-pytest-runner' 'python2-pytest-runner' 'python-pretend' 'python2-pretend' 'python-coverage' 'python2-coverage')
source=("git+https://github.com/pypa/packaging.git#tag=$pkgver")
md5sums=('SKIP')

prepare() {
  cp -a $_pkgname{,-py2}
}

build() {
  cd "${srcdir}/${_pkgname}"
  python setup.py build

  cd "${srcdir}/${_pkgname}-py2"
  python2 setup.py build
}

check() {
  cd "${srcdir}/${_pkgname}"
  python setup.py ptr

  cd "${srcdir}/${_pkgname}-py2"
  python2 setup.py ptr
}

package_python-packaging() {
  depends=('python-pyparsing' 'python-six')

  cd "${srcdir}/${_pkgname}"
  python setup.py install --root "$pkgdir"
}

package_python2-packaging() {
  depends=('python2-pyparsing' 'python2-six')

  cd "${srcdir}/${_pkgname}-py2"
  python2 setup.py install --root "$pkgdir"
}
