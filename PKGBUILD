pkgname=perl-socket6
pkgver=0.25
pkgrel=1
pkgdesc="A getaddrinfo/getnameinfo support module"
arch=('x86_64')
url='http://search.cpan.org/dist/Socket6'
license=('PerlArtistic' 'GPL')
depends=('perl')
options=('!emptydirs')
source=(http://search.cpan.org/CPAN/authors/id/U/UM/UMEMOTO/Socket6-$pkgver.tar.gz)
sha1sums=('4499bd5b5150bd44be79238df348d89ea228f5a6')

build() {
  cd Socket6-$pkgver
  perl Makefile.PL INSTALLDIRS=vendor
  make
}

check() {
  cd Socket6-$pkgver
  make test
}

package() {
  cd Socket6-$pkgver
  make DESTDIR="$pkgdir" install
# template start; name=perl-binary-module-dependency; version=1;
if [[ $(find "$pkgdir/usr/lib/perl5/" -name "*.so") ]]; then
	_perlver_min=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]);')
	_perlver_max=$(perl -e '$v = $^V->{version}; print $v->[0].".".($v->[1]+1);')
	depends+=("perl>=$_perlver_min" "perl<$_perlver_max")
fi
}
