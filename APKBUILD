# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=internetarchive
pkgver=1.8.4
pkgrel=0
pkgdesc="Python and Command-Line Interface to Archive.org"
url="https://archive.org/services/docs/api/internetarchive"
arch="all"
license="APGL-3"
depends="python"
makedepends="py-setuptools python2-dev python3-dev"
install=""
subpackages="py2-${pkgname#py-}:_py2 py3-${pkgname#py-}:_py3 $pkgname-dev $pkgname-doc"
source="internetarchive-$pkgver.tar.gz::https://github.com/jjjake/internetarchive/archive/v$pkgver.tar.gz"
builddir="$srcdir/$pkgname-$pkgver"

build() {
	cd "$builddir"
	python2 setup.py build
	python3 setup.py build
}

package() {
	mkdir -p "$pkgdir"
}


_py() {
	local python="$1"
	pkgdesc="$pkgdesc ${python#python}"
	depends="$depends $python"
	subpkgarch="all"
	install_if="$pkgname=$pkgver-r$pkgrel $python"

	cd "$builddir"
	$python setup.py install --prefix=/usr --root="$subpkgdir"
}

_py2() {
	replaces="$pkgname"
	depends="${depends//py-/py2-}"
	_py python2
}

_py3() {
	depends="${depends//py-/py3-}"
	_py python3
}

sha512sums="fb38e63cd9558e7bee385304eb8e67efc44c38e58d8f89f776d05edb69f1f92bb21a9294fc9929b9d809566489782542450339f877b466f5a08d8eede041fa9c  internetarchive-1.8.4.tar.gz"
