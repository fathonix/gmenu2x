# Maintainer: Aldo Adirajasa Fathoni (fathonix) <aldo.alfathoni@gmail.com>

pkgname=gmenu2x
pkgver=0.11
pkgrel=1
pkgdesc='GMenu2X is a replacement for the official frontend for the GP2X. PC version.'
arch=('i386' 'amd64' 'armel' 'armhf' 'arm64')
depends=(
    'libsdl1.2debian'
    'libsdl-image1.2'
    'libsdl-gfx1.2-5'
    'libsdl-ttf2.0-0'
    'libfreetype6'
    'libpng16-16'
)
makedepends=(
    'build-essential'
    'libsdl1.2-dev'
    'libsdl-image1.2-dev'
    'libsdl-gfx1.2-dev'
    'libsdl-ttf2.0-dev'
    'libfreetype-dev'
    'libpng-dev'
    'findutils'
)
license=('GPL2')
url='https://github.com/mtorromeo/gmenu2x'
source=(
    "${url}/archive/refs/tags/v${pkgver}.tar.gz"
    "gmenu2x-fix-unistd.patch"
    "gmenu2x-fix-Makefile.patch"
    "gmenu2x-wrapper"
)
sha256sums=(
    'SKIP'
    '88ad78e6eddcaf1f02f7155d851e1bf2b96ccac1e9b289934bd97e8d68c800d3'
    'd2812b031d348311b1b42f20607bccc1fb61d2be09e76062994ba7546ddf269d'
    '883c1d4582ffcb5cf8850883ae77a2095e01089f158652e57ad939a0703cc6af'
)

build() {
    cd "${pkgname}-${pkgver}"
    patch -p1 < ../gmenu2x-fix-unistd.patch
    patch -p1 < ../gmenu2x-fix-Makefile.patch
    make
}

package() {
    install -Dm 755 gmenu2x-wrapper "${pkgdir}/usr/bin/gmenu2x"

    cd "${pkgname}-${pkgver}"
    make dist
    cd dist/pc/gmenu2x
    install -Dm 755 gmenu2x "${pkgdir}/usr/libexec/gmenu2x"
    find . -type f -not -name gmenu2x -exec \
      install -Dm 644 "{}" "${pkgdir}/usr/share/gmenu2x/{}" \;
}

# vim: set sw=4 expandtab:
