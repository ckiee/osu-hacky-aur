# Maintainer: emersion <contact@emersion.fr>
# Contributor: ValdikSS <iam@valdikss.org.ru>

pkgname=osu
pkgver=20180917
pkgrel=2

source=("http://m1.ppy.sh/r/osu!install.exe"
	"directsound-latency.reg"
	"osu.desktop"
	"osulauncher"
	"osu.png"
	"osu.env"
	"https://github.com/lutris/wine/releases/download/lutris-osu-1/wine-lutris-osu-1-x86_64.tar.xz")

sha512sums=('SKIP'
            '6b63f51553d39a8a80ef3f0223a9a884c7c779a13a8d0c14f0792b6661e6613dfa2c8bd15d60aba6d5d3a3845fa82080b7385fd8e11af83b38fdc7ce074a65e9'
            'fdc25f7444735c0d19045f061ab94ac94f59b76f3ecea918ede281dd3f83de93985277e45972dea6397d521cc054a7f348b0c124d28efd91217d94e45285772b'
            'c50ce0eb071d661d112704ae4d0982c03f1e5d664fe3810e8270db4607708db861c80cf9859902ae30bfae819f48631f2c4e365ab0e35da8626a38e081b82f9e'
            'fbcd240a07dcec912f3f266797d2aac1f70e1854b25a902a77f12362a6320ddc6e3db83b43c7d675e6f4b652f9a2c1a60e74ffd86cf52ee03416e661720fc5a9'
            'd978eaa3bd4362a89804326196e2231a675eb2ce099e078ae24556f114050aa75421605838dad994dd57c54e9399eec5410ac73550778443561725cf3417dc5e'
            '7c73f8782b748ca3b554dfb06f3ae15c01c630c7af38cfdf38e2b85e1bb65d545d94b70ff8e1431c6bc953d9443615c52964f0f60eb980720945445e06a32c7b')

pkgdesc="Freeware rhythm video game"
url="http://osu.ppy.sh"
arch=(i686 x86_64)
license=(custom)
install=osu.install

depends=(wine winetricks)
depends_x86_64=(lib32-alsa-lib lib32-gnutls)

package() {
    cd "$srcdir"

    install -Dm644 osu.desktop "$pkgdir/usr/share/applications/osu.desktop"
    install -Dm644 osu.png "$pkgdir/opt/osu/osu.png"
	install -Dm644 osu.env "$pkgdir/etc/osu.env"
    install -Dm644 directsound-latency.reg "$pkgdir/opt/osu/directsound-latency.reg"
    install -Dm755 osulauncher "$pkgdir/opt/osu/"
    mkdir -p "$pkgdir/usr/bin"
    ln -s /opt/osu/osulauncher "$pkgdir/usr/bin/osu"
    install -Dm775 osu\!install.exe "$pkgdir/opt/osu/game/osu!install.exe"
    #mkdir "$pkgdir/opt/osu/game/"
    #cd "$pkgdir/opt/osu/game/"
    #tar xjpf "$srcdir/osu.tar.bz2"
    chown -R root:games "$pkgdir/opt/osu/game/"
    chmod g+s "$pkgdir/opt/osu/game/"
    chmod g+w "$pkgdir/opt/osu/game/"

	cp -r lutris-osu-*-x86_64 "$pkgdir/opt/osu/lutris-osu"
}
