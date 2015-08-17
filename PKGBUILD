#Maintainer: Alexey Stukalov <astukalov@gmail.com>
pkgname=smartgithg-ea
_pkgname=smartgit
pkgver=6.5_rc_3
pkgrel=1
pkgdesc="Git/Hg GUI client written in Java. Early Access Series"
arch=("any")
url="http://www.syntevo.com/smartgit/early-access"
license=('custom')
depends=("java-runtime" "desktop-file-utils" "sh" "git" "gtk2")
optdepends=("mercurial: hg repositiories support")
provides=(smartgithg=$pkgver)
# package version as it appears in the name of tar.gz archive file
_pkgver=${pkgver//_/-}
_pkgver=${_pkgver//\./_}
# folder within tar.gz archive
_pkgfolder="$_pkgname"
source=(http://www.syntevo.com/download/${_pkgname}/${_pkgname}-generic-${_pkgver}.tar.gz
        smartgit-ea.desktop)
install="smartgit-ea.install"
md5sums=('f046626aa4544175e54f7c0b3e608253'
         '72d982c9978e84253deaa17ac8dba847')

package() {
    cd "$srcdir"

    #install -D -m644 "${_pkgfolder}"/licenses/* "${pkgdir}/usr/share/licenses/${pkgname}"
    mkdir -p "${pkgdir}"/opt
    cp -R "${_pkgfolder}" ${pkgdir}/opt/${pkgname} || return 1

    install -D -m644 smartgit-ea.desktop "${pkgdir}"/usr/share/applications/${pkgname}.desktop

    # create link in /usr/bin
    cd ${pkgdir}
    chmod 755 opt/${pkgname}/bin/smartgit.sh
    mkdir -p usr/bin
    ln -s /opt/${pkgname}/bin/smartgit.sh usr/bin/${pkgname}
}
