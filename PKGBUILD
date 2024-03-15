
pkgname=slack-desktop
pkgver=4.36.140
pkgrel=1
pkgdesc="Slack Desktop (Beta) for Linux"
arch=('x86_64')
url="https://slack.com/downloads"
license=('custom')
depends=('gtk3' 'libsecret' 'libxss' 'nss' 'xdg-utils')
source=("https://downloads.slack-edge.com/releases/linux/${pkgver}/prod/x64/${pkgname}-${pkgver}-amd64.deb")
noextract=("${pkgname}-${pkgver}-amd64.deb")


b2sums=('2af0c4069d56c8dea6938034cf913414e3b865965bed0d3fce55bab5788c2bc1de8cf8824cd25979adfcd401b0132b45a6212507d7c6c04bbc6b0576de53f790')

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
