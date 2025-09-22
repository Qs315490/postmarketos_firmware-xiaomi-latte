pkgname=firmware-xiaomi-latte
pkgver=1.0
pkgrel=1
pkgdesc="firmware for tablets based on Mipad2"
url="https://github.com/Qs315490/latte_kernel_6.10"
arch="x86_64"
license="MIT"
source="
	alsa-ucm-conf/cht-bsw-rt5659.conf
	alsa-ucm-conf/HiFi.conf
    firmware/brcm/BCM4356A2.hcd
    keyboard/keyboard.hwdb
"
options="!check !archcheck"
depends="
	linux-firmware-i915
	linux-firmware-brcm
	linux-firmware-intel
	libva-intel-driver
	intel-ucode
	mesa-vulkan-intel
"

package() {
	# Firmware for Xiaomi Mi Pad 2
	mkdir -p "$pkgdir/lib"
	cp -r "firmware" "$pkgdir/lib/"

	# ALSA Use Case Manager configuration for Xiaomi Mi Pad 2
	mkdir -p "$pkgdir/usr/share/alsa/ucm2/Intel/cht-bsw-rt5659"
	install -Dm644 "alsa-ucm-conf/cht-bsw-rt5659.conf" \
		"$pkgdir/usr/share/alsa/ucm2/Intel/cht-bsw-rt5659/cht-bsw-rt5659.conf"
	install -Dm644 "alsa-ucm-conf/HiFi.conf" \
		"$pkgdir/usr/share/alsa/ucm2/Intel/cht-bsw-rt5659/HiFi.conf"
	mkdir -p "$pkgdir/usr/share/alsa/ucm2/conf.d/cht-bsw-rt5659"
	ln -sf ../../Intel/cht-bsw-rt5659/cht-bsw-rt5659.conf \
		"$pkgdir/usr/share/alsa/ucm2/conf.d/cht-bsw-rt5659/cht-bsw-rt5659.conf"
	mkdir -p "$pkgdir/etc/modules-load.d"
	echo "snd-soc-rt5659" > "$pkgdir/etc/modules-load.d/00-xiaomi-latte.conf"

	# on Screen Touch Keyboard configuration for Xiaomi Mi Pad 2
	mkdir -p "$pkgdir/usr/lib/udev/hwdb.d"
	install -Dm644 "keyboard/keyboard.hwdb" \
		"$pkgdir/usr/lib/udev/hwdb.d/61-keyboard.hwdb"
}

sha512sums="
10c8139304f6caa96f9afa49af49b3ddcb9e450f488b0a977b01e7ad2c98be07d7bf28135b2668181bfbd9ebdc6e34979036e7f33f768daa023d2fa4cf0b0d8a  cht-bsw-rt5659.conf
d5c5f43b8d1183eccd84c928ed889a0df9571a63bf76634b1b496108386212bdc4d9a88093555ac0e2bf51a9c72bc89acc193eafffade31dd3399d9da0844e7a  HiFi.conf
fa34874f938d7532d80ee3395d93f1c957260c08f77671074266e3c3c3ca7190b8200668af96b0861ed5b961522d5088921cd3d4af236d287945a7527f75f916  BCM4356A2.hcd
125b348af270ed10c3bd17766f2194b40a65ae0204675e4269579174cee6f9db3f498bce16d4361a90031275aaf57a888972a9713c5d12bed22036fa34bff017  keyboard.hwdb
"
