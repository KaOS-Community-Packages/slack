
pkgname=slack-desktop
pkgver=4.27.156
pkgrel=1
pkgdesc="Slack Desktop (Beta) for Linux"
arch=('x86_64')
url="https://slack.com/downloads"
license=('custom')
depends=('gtk3' 'libsecret' 'libxss' 'nss' 'xdg-utils')
source=("https://downloads.slack-edge.com/releases/linux/${pkgver}/prod/x64/${pkgname}-${pkgver}-amd64.deb")
noextract=("${pkgname}-${pkgver}-amd64.deb")


b2sums=('b7d457fcb6a2518eaea7efc4d7b43f01f8c1da8a1218d3c2c2c14e195004102be344c6f4e2b60dd4f4677e53ea976cb7b0b102e3e0eec385df881eecdee4a7cd')

package() {
    bsdtar -O -xf "slack-desktop-${pkgver}"*.deb data.tar.xz | bsdtar -C "${pkgdir}" -xJf -

    # Permission fix
    find "${pkgdir}" -type d -exec chmod 755 {} +

    # Remove all unnecessary stuff
    rm -rf "${pkgdir}/etc"
    rm -rf "${pkgdir}/usr/lib/slack/src"
    rm -rf "${pkgdir}/usr/share/lintian"
    rm -rf "${pkgdir}/usr/share/doc"

    # Move license
    install -dm755 "${pkgdir}/usr/share/licenses/${pkgname}"
    mv "${pkgdir}/usr/lib/slack/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}"
    ln -s "/usr/share/licenses/${pkgname}/LICENSE" "${pkgdir}/usr/lib/slack/LICENSE"
}
