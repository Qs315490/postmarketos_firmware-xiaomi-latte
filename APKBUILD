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
    firmware/brcm/brcmfmac4356-pcie.txt
	firmware/i915/huc_gen8.bin
    firmware/intel/ipu/shisp_2401a0_v21.bin
    firmware/intel/fw_sst_22a8.bin
    keyboard/keyboard.hwdb
"
options="!check !archcheck"
depends="
	linux-firmware-i915
	linux-firmware-brcm
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
49ee1cfa2803728c00069fe5477dbb77da15f78e4a965e56a248348ed0cb9c0e201c0424f50c76940974a372671e6e2c7ba66daba4073cd7665329a739214bdb  brcmfmac4356-pcie.txt
c578770fb44df9650d30d6ed061c16696ab42c46ea9de4a78dde365c9c5487cd6da3bd896819b68d69b2ad215861b48a8fe6899839eaf4e7e33ad13d0855bf00  huc_gen8.bin
0dceb4d3dac455dfeb116c6f2ba2ffe73f5f96dcdeb74a198fb7fb82f0c4e7977803021b8a23bd9312b4f6f83a3c2f062cca116c8001721a0342b16ffab6f38b  shisp_2401a0_v21.bin
61425b4417e9e24003787e50482c62e0b8dd4c7678e91736e92af216de33c0e02d080c35927921cce30aded4db72586115a5a930f39348eabc166a345ee475f0  fw_sst_22a8.bin
a365f2e2aaa9b4784d8ca97badb1e1e259ca5cc391e728e2ad45432d63c5f0c262176c07d3ab55913794a183e44be54d71a777a638ae190c4ccc4240f8ce93f3  keyboard.hwdb
"
