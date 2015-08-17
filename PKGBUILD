# Maintainer: Max Pray a.k.a. Synthead <synthead@gmail.com>

pkgname=perl-text-wrapper
_cpanname="Text-Wrapper"
pkgver=1.03
pkgrel=1
pkgdesc="Simple word wrapping routine"
arch=('any')
url="http://search.cpan.org/~cjm/$_cpanname"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.5.0')
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/C/CJ/CJM/$_cpanname-$pkgver.tar.gz")
md5sums=('d0644d4e504a75b9ebbff3407fc353c8')

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
	cd "$srcdir/$_cpanname-$pkgver"
	export \
		PERL_MM_USE_DEFAULT=1 \
		PERL_AUTOINSTALL=--skipdeps \
		PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
		PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
		MODULEBUILDRC=/dev/null
}

build() {
	prepareEnvironment
	/usr/bin/perl Makefile.PL
	make
}

check() {
	prepareEnvironment
	make test
}

package() {
	prepareEnvironment
	make install

	# Remove "perllocal.pod" and ".packlist".
	find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
