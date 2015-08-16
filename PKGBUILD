# Original contributor: kei (Kevin)
# Mantainer: Martín Cigorraga Müller <msx (@) archlinux (dot) us>


pkgname=kdeplasma-applets-tomatoid-git
pkgver=20141125
pkgrel=1
pkgdesc="A Pomodoro plasmoid made in QML"
arch=('i686' 'x86_64')
url='https://github.com/arthurtaborda/Tomatoid'
license=('GPL')
depends=('kdebase-workspace' 'qtmobility' 'pulseaudio')
makedepends=('git' 'cmake' 'automoc4')
install='tomatoid.install'

_gitroot="https://github.com/arthurtaborda/Tomatoid.git"
_gitname="Tomatoid"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
}

package() {
  cd "${srcdir}/${_gitname}"
  install_folder="${pkgdir}/usr/share/apps/plasma/plasmoids/tomatoid/"
  install -d "${install_folder}"/contents/{code,config,data,images,locale,ui}
  install -m644 metadata.desktop "${install_folder}"
  install -m644 contents/code/* "${install_folder}"/contents/code/
  install -m644 contents/config/* "${install_folder}"/contents/config/
  install -m644 contents/data/* "${install_folder}"/contents/data/
  install -m644 contents/images/* "${install_folder}"/contents/images/
  install -m644 contents/locale/*.{sh,pot} "${install_folder}"/contents/locale/
  install -d "${install_folder}"/contents/locale/pt_BR/LC_MESSAGES/
  install -m644 contents/locale/pt_BR/LC_MESSAGES/* "${install_folder}"/contents/locale/pt_BR/LC_MESSAGES/
  install -m644 contents/ui/*.{ui,qml} "${install_folder}"/contents/ui/
  install -Dm644 metadata.desktop \
    "${pkgdir}"/usr/share/kde4/services/plasma-applet-tomatoid.desktop 
}
