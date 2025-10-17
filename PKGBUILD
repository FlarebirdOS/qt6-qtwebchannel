pkgname=qt6-qtwebchannel
pkgver=6.10.0
pkgrel=2
pkgdesc="Provides access to QObject or QML objects from HTML clients for seamless integration of Qt applications with HTML/JavaScript clients"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'qt6-qtbase'
    'qt6-qtdeclarative'
)
makedepends=(
    'cmake'
    'git'
    'ninja'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(c45c809aee77855d267dd7ea84e38fc167276403c9288f132f3980a4b7c9873f)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}

