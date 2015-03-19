# Maintainer: ungleich GmbH <archlinux@ungleich.ch>

pkgname=one-context
pkgver=4.8.1
pkgrel=4
pkgdesc='Opennebula Contextualisation'
arch=('any')
url='http://dev.opennebula.org/projects/opennebula/files'
license=('Apache')
depends=()
source=("http://dev.opennebula.org/attachments/download/815/one-context_${pkgver}.rpm"
    "one-context.patch")
install=one-context.install

prepare() {
    patch -p1 < one-context.patch
}

build() {
    mkdir -p usr/lib/systemd/

    cat << eof > usr/lib/systemd/one-context
[Unit]
Description=$pkgdesk
Requires=network.target
After=network.target

[Service]
Type=oneshot

ExecStart=/etc/init.d/one-context

StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=one-context

RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
eof
}


package() {
    mv ${srcdir}/etc ${pkgdir}
    mv ${srcdir}/usr ${pkgdir}
}
md5sums=('87fc768ee92eaaa5c78eee7b9646482d'
         '2e82a9d0c616fb2153b85ca5d7d5acac')
