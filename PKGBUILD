# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=python2-tlslite
pkgver=0.4.8
pkgrel=1
pkgdesc="SSL/TLS library in pure Python supporting RSA and SRP ciphersuites"
arch=('any')
depends=('python2')
makedepends=('python2-setuptools')
optdepends=('python2-crypto: fast RSA operations and fast ciphers'
            'python2-gmpy: fast RSA and SRP operations'
            'python2-m2crypto: fast RSA operations and fast ciphers'
            'python2-tackpy: run an X.509 server using TACK')
url="http://trevp.net/tlslite"
license=('custom:public domain' 'BSD')
options=(!emptydirs)
source=(https://pypi.python.org/packages/source/t/${pkgname#python2-}/${pkgname#python2-}-$pkgver.tar.gz)
md5sums=('36c13858ea63f262c4e4291c2f9ae38f')
sha256sums=('d9b447048a322c70df800f540ab577c93ecf20de52c0a02c8621176e4733bdbb')

prepare(){
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Fixing Python version...'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/python#/usr/bin/python2#g'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/env python#/usr/bin/env python2#g'
}

build() {
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Building...'
  python2 setup.py build
}

package() {
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Installing license...'
  install -Dm 644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  msg 'Installing docs...'
  install -Dm 644 README "$pkgdir/usr/share/doc/$pkgname/README"

  msg 'Installing...'
  python2 setup.py install --root="$pkgdir" --optimize=1
}
