# Maintainer: zach <zach {at} zach-adams {dot} com>
# Contributor: Gordian Edenhofer <gordian.edenhofer[at]yahoo[dot]de

pkgname=gtk-theme-solarc-git
_pkgname=solarc-theme
_pkgauthor=schemar
_gnomeversion=3.32
pkgver=817.3e68bc0
pkgrel=1
pkgdesc="A flat theme with transparent elements. Based on the Arc theme: https://github.com/NicoHood/arc-theme"
arch=('any')
url="https://github.com/${_pkgauthor}/${_pkgname}"
license=('GPL3')
depends=('gtk3' 'gtk-engine-murrine')
makedepends=('git' 'wget' 'inkscape' 'sassc' 'optipng')
source=("${_pkgname}::git+https://github.com/${_pkgauthor}/${_pkgname}.git")
sha256sums=('SKIP')
conflicts=('gtk-theme-solarc')
provides=('gtk-theme-solarc')

pkgver() {
    cd "${srcdir}/${_pkgname}"
    echo "$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

build() {
    cd "${srcdir}/${_pkgname}"
    ./solarize.sh
    cd $(ls | grep "arc-theme-" | tail -1)
    ./autogen.sh --prefix=/usr --with-gnome-shell=${_gnomeversion}
    make
}

package() {
    cd "${srcdir}/${_pkgname}$(ls | grep "arc-theme-" | tail -1)"
    make DESTDIR="${pkgdir}" install
}
