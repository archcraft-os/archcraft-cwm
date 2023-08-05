# Maintainer: Aditya Shakya <adi1090x@gmail.com>

pkgname=archcraft-cwm
pkgver=1.0
pkgrel=0
pkgdesc="CWM Configurations for Archcraft"
url="https://github.com/archcraft-os/archcraft-cwm"
arch=('any')
license=('GPL3')
makedepends=('git')
depends=('cwm'
		'alacritty' 'thunar' 'geany'
		'rofi' 'dunst'
		'mpd' 'mpc'
		'maim' 'xclip' 'viewnior'
		'ksuperkey' 
		'betterlockscreen'
		'xfce4-power-manager' 
		'xsettingsd'
		'hsetroot'
		'wmname'
		'pulsemixer' 'light' 'xcolor'
)
conflicts=()
provides=("${pkgname}")
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
	cp -af ../files/. ${srcdir}
}

package() {
	local _config=${pkgdir}/etc/skel/.cwm
	mkdir -p "$_config"

	# Copy cwm config files
	cp -r ${srcdir}/alacritty 		"$_config"
	cp -r ${srcdir}/scripts 		"$_config"
	cp -r ${srcdir}/theme 			"$_config"

	chmod +x "$_config"/scripts/*
	chmod +x "$_config"/theme/polybar.sh
	chmod +x "$_config"/theme/polybar/launch.sh
	chmod +x "$_config"/theme/polybar/scripts/bluetooth.sh

	install -Dm 644 dunstrc   				"$_config"/dunstrc
	install -Dm 644 picom.conf   			"$_config"/picom.conf
	install -Dm 644 picom-ibhagwan.conf   	"$_config"/picom-ibhagwan.conf
	install -Dm 644 picom-jonaburg.conf   	"$_config"/picom-jonaburg.conf
	install -Dm 644 picom-original.conf   	"$_config"/picom-original.conf
	install -Dm 644 xsettingsd   			"$_config"/xsettingsd

	install -Dm 644 .cwmrc   			      ${pkgdir}/etc/skel/.cwmrc

	install -Dm 755 run-cwm   			      ${pkgdir}/usr/local/bin/run-cwm
	install -Dm 644 archcraft-hook-cwm.hook   ${pkgdir}/usr/share/libalpm/hooks/archcraft-hook-cwm.hook
}
