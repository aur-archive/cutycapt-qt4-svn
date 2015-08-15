# Maintainer:  trashstar <trash@ps3zone.org>
# Contributor: Evan Teitelman <teitelmanevan at gmail dot com>
# Contributor: Renan Fernandes <renan@kauamanga.com.br>

pkgname=cutycapt-qt4-svn
pkgver=10
pkgrel=2
pkgdesc="A Qt and WebKit based command-line utility that captures WebKit's rendering of a web page."
arch=('i686' 'x86_64')
url="http://cutycapt.sourceforge.net/"
license=('GPL')
depends=('qtwebkit')
makedepends=('subversion')
provides=('cutycapt')
conflicts=('cutycapt')
source=('svn://svn.code.sf.net/p/cutycapt/code/'
        'cutycapt.patch')
md5sums=('SKIP'
         '29ee690d164564a21bad3cfa30fef5a7')

pkgver() {
    cd "$SRCDEST/code"
    svnversion | tr -d [A-z]
}

build() {
    cd "${srcdir}/code/CutyCapt"

    # The file we are patching has crlf line endings so we gave the patch file
	#  CRLF line endings and tell patch to not convert the patch line endings
	#  back to LF by passing it the '--binary' flag. There may be a better way
	#  to do this.
	patch --binary -Np0 < "${srcdir}/cutycapt.patch"

	qmake-qt4
	make
}

package() {
	cd "${srcdir}/code/CutyCapt"
	install -m755 -d "${pkgdir}/usr/bin"
	install -m755 "CutyCapt" "${pkgdir}/usr/bin/"
}
