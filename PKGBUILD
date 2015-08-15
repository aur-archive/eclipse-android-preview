# Maintainer: Joel Pedraza <joel@joelpedraza.com>
# Contributor: Jakub Schmidtke <sjakub-at-gmail-dot-com>
# Contributor: Forrest L <cybercyst at gmail com>
# Contributor: Michael P <ptchinster@archlinux.us>
# Contributor: Marcin "eXine" M. <exine@jun.pl>
# Contributor: Artyom Smirnov <smirnoffjr@gmail.com>
# Contributor: Ashok `ScriptDevil` Gautham <ScriptDevil@gmail.com>
# Contributor: Laszlo Papp <djszapi2 at gmail com>
# Contributor: Antonio Santos <asantos at gmail dot com>

pkgname=eclipse-android-preview
pkgver=21.1.0_rc3
pkgrel=1
pkgdesc='Eclipse plugin for Android Preview'
url='http://dl.google.com/dl/android/eclipse-preview/index.html'
license=('Apache' 'BSD' 'EPL' 'LGPL')
arch=('any')
depends=('android-sdk-preview>=r21.1_rc2' 'java-environment>=6' 'eclipse>=3.6.2' 'eclipse-wtp')
provides=('eclipse-android=21.1.0')
conflicts=('eclipse-android')
makedepends=('unzip')
options=('!strip')
source=("http://dl.google.com/android/eclipse-preview/ADT-${pkgver}.zip" "LICENSE.kxml2")
sha1sums=('7e2e4b257c76097c07ed8577981d379c94651c45'
          'c0a96dc032bb53e2921200c85f5cf650e49878e9')

package() {
  _dest="${pkgdir}/usr/share/eclipse/dropins/android/eclipse"

  cd "${srcdir}"

  # Features
  for _f in features/*.jar; do
    _dir="${_dest}/${_f/.jar}"
    mkdir -p "${_dir}"
    unzip "${_f}" -d "${_dir}"
  done

  # Plugins
  for _p in plugins/*.jar; do
    install -Dm644 "${_p}" "${_dest}/${_p}"
  done

  install -D -m644 LICENSE.kxml2 "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.kxml2"
}
