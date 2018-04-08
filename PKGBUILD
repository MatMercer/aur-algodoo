# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Mateus Mercer <mateusmercer@gmail.com>
pkgname=algodoo
_pkgname=Algodoo
pkgver=2.1.0
_pkgver=2_1_0
pkgrel=1
epoch=
pkgdesc="Algodoo is a unique 2D-simulation software from Algoryx Simulation AB (Using Wine)."
arch=("any")
url=""
license=('custom:Algodoo')
groups=()
depends=('wine'
	 'innoextract')
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
_alg="${_pkgname}_${_pkgver}-Win32.exe"
_wine="wine-1.8-rc1"
source=("${_alg}::http://www.algodoo.com/download"
	"LICENSE"
	)
noextract=()
sha256sums=("3e65d18c63b20c17aaedd5c96f9751d914dc5e024ef001fc5cf569b94255caa4"
	    "3a46622a459bd0148d52988a7d5bcd7432facfe6af30b33a2f6db5f4f04f5bb2"
	    )
validpgpkeys=()

package() {
	# Create common folders
	mkdir -p "${pkgdir}/usr/share/"

	# Extract installer using innoextract
	innoextract "${_alg}" --output-dir "${pkgdir}/usr/share/"

	# Correct filesystem perms
	find "${pkgdir}" -type d -execdir chmod 755 {} +

	# Install the license
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/$pkgname/LICENSE"
}
