# Contributor: Kazuo Teramoto <kaz.rag gmail com>
# Contributor: scj <scj archlinux us>
# Contributor: tracer <jcdenton513 gmail com>
# Maintainer: aksr <aksr at t-com dot me>
pkgname=orpie
pkgver=1.5.2
pkgrel=11
epoch=
pkgdesc="https://github.com/pelzlpj/orpie"
arch=('i686' 'x86_64')
url="http://pessimization.com/software/orpie/"
license=('GPL')
groups=()
depends=('ncurses' 'gsl')
makedepends=('ocaml' 'gsl' 'camlp4')
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("https://github.com/pelzlpj/${pkgname}/releases/download/release-${pkgver}/${pkgname}-${pkgver}.tar.gz"
    'associated_legendre.patch'
    'caml__frame_undeclared.patch'
    'ellint_d_sf3.patch'
    'Makefile_in.patch')
noextract=()
md5sums=('1fd02e75549cca954cebbd13271ea7f5'
         '90d6d12dc90f817c7b18e5dc065ff3c8'
         'f4621a5a9ad6ae44a8b88bd2618b9890'
         '5f2f31bcc7739ee313b4e67de52adaff'
         '540d2305c5cdb24328966f0566bcc63d')
sha1sums=('9786df20fb272fd36f87868bed04cab504602282'
          '8144c29af06eb2e8e58d652d58c69494b4bec3f9'
          '70900a57240b740bc661c854290c30dd50a7299b'
          '6a0f75d0df1f44cc45d7d46b6228b594ad51f3d7'
          '8222ac186973419a359912acf9724692570256ad')
sha256sums=('de557fc7f608c6cb1f44a965d3ae07fc6baf2b02a0d7994b89d6a0e0d87d3d6d'
            'abc2bd53a85ce80cc1c3eeec62719854a8ce3be7213a9a7c1d909c0f6ed0a96a'
            '8983e40bb3a046eaf82e16c8af882f5b4f3146d228cb5bdfcc977e83032d4160'
            '5cb9e463ce77740731f7bdee3ba591d89f7cef400ce2dbb20cc9a48563a869d5'
            'ab02da769faf99159e7e5cbb81e0551adb0a91bdc46f7e6d88f83a7b45b828a6')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  patch -p1 -i $srcdir/associated_legendre.patch
  patch -p1 -i $srcdir/caml__frame_undeclared.patch
  patch -p1 -i $srcdir/ellint_d_sf3.patch
  patch -p1 -i $srcdir/Makefile_in.patch
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --mandir=/usr/share/man --sysconfdir=/etc
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install
  install -Dm644 doc/manual.pdf $pkgdir/usr/share/doc/$pkgname/manual.pdf
  install -Dm644 COPYING $pkgdir/usr/share/licenses/$pkgname/COPYING
}

