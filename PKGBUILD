# Maintainer: Fredy García <frealgagu at gmail dot com>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Allan McRae <allan@archlinux.com>
# Contributor: gyo <nucleogeek@gmail.com>

pkgname=sdl_pango
pkgver=0.1.2
pkgrel=10
pkgdesc="Connects Pango to SDL"
arch=("x86_64")
url="http://sdlpango.sourceforge.net/"
license=("LGPL")
depends=("pango" "sdl")
source=(
  "${pkgname}-${pkgver}.tar.gz::https://downloads.sourceforge.net/sourceforge/${pkgname/_/}/SDL_Pango-${pkgver}.tar.gz"
  "SDL_Pango-${pkgver}-API-adds.patch"
  "matrix_declarations.patch"
  "SDL_Pango-0.1.2-fedora-c99.patch::https://src.fedoraproject.org/rpms/SDL_Pango/raw/rawhide/f/SDL_Pango-0.1.2-fedora-c99.patch"

)
sha256sums=(
  "7f75d3b97acf707c696ea126424906204ebfa07660162de925173cdd0257eba4"
  "5a989c7acb539fce640323d3995cca8913a4b8869f5c690b78501ec6b5c86d5d"
  "cfff600cae86bf75070f8921da565210409efba318f45361b34489ac29298bc5"
  "741456f9759852da480eba98656afc69cf2c9bdc8681d1b4c2a577fdb6a6c21d"
)

prepare() {
  cd "${srcdir}/SDL_Pango-${pkgver}"

  patch -Np0 -i "${srcdir}/SDL_Pango-${pkgver}-API-adds.patch"
  patch -Np1 -i "${srcdir}/matrix_declarations.patch"
  patch -Np1 -i "${srcdir}/SDL_Pango-0.1.2-fedora-c99.patch"
}

build() {
  cd "${srcdir}/SDL_Pango-${pkgver}"

  ./configure --prefix=/usr
  make
}

package() {
  cd "${srcdir}/SDL_Pango-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
