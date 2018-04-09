# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Mateus Mercer <mateusmercer@gmail.com>
pkgname=algodoo
_pkgname=Algodoo
pkgver=2.1.0
_pkgver=2_1_0
pkgrel=2
pkgdesc="Algodoo is a unique 2D-simulation software from Algoryx Simulation AB (Using Wine)."
arch=("any")
url="http://algodoo.com"
license=('custom:Algodoo')
depends=('wine'
	 'innoextract'
	 'lib32-nvidia-utils'
	 'winetricks'
	 'desktop-file-utils')

_alg="${_pkgname}_${_pkgver}-Win32.exe"
_wine="wine-1.8-rc1"
source=("http://www.algodoo.com/download/${_alg}"
	"LICENSE"
	"algodoo.sh"
	"algodoo.desktop"
	"algodoo.png"
	)
sha256sums=("3e65d18c63b20c17aaedd5c96f9751d914dc5e024ef001fc5cf569b94255caa4"
	    "3a46622a459bd0148d52988a7d5bcd7432facfe6af30b33a2f6db5f4f04f5bb2"
	    "7d29ce62408ee798a56110575474b2ee69bc73b88a7712d864b141ad7dc6fca0"
	    "e4afe153053db562210ef2c11d92a17ec3763b39426efc3e92e74694a7556147"
	    "0f7e995cd90df87236404db4c28789e23eef7341cc47f321f1ea6ce30fa913f1"
	    )
package() {
	# Create common folders
	mkdir -p "$pkgdir/usr/share/algodoo"

	# Extract installer using innoextract
	innoextract "${_alg}" --output-dir "$pkgdir/usr/share/algodoo"

	# Correct filesystem perms
	find "$pkgdir"/usr/share -type f -exec chmod 644 "{}" \;
	find "$pkgdir"/usr/share -type d -exec chmod 755 "{}" \;

	# Install the license
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

	# Install the script
	install -Dm755 algodoo.sh "$pkgdir/usr/bin/algodoo"

	# Install the icon
	install -Dm644 algodoo.png "$pkgdir/usr/share/pixmaps/algodoo.png"

	# Install the .desktop
	install -Dm644 algodoo.desktop "$pkgdir/usr/share/applications/algodoo.desktop"

	# Core fonts, needed for Algodoo
	sudo -H -u $USER bash -c 'winetricks -q corefonts'

	# C++ 2008 native runtime, needed for Algodoo
	sudo -H -u $USER bash -c 'winetricks -q vcrun2008'
}
