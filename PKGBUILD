# Maintainer: Gian Balex <gianbalexdev at gmail dot com>
pkgname=gitty-git
pkgver=20120530
pkgrel=1
pkgdesc="Gitty is a powerfull command-line tool to semplify git-commands life!"
arch=('i686' 'x86_64')
url="https://github.com/gianbalex/gitty"
license=('AGPL')
groups=('gitty')
depends=('php')
makedepends=('git')

_gitroot="http://github.com/gianbalex/gitty.git"
_gitname="gitty"

_installto="$pkgdir/usr/share/pear/$_gitname"

_phpscript="/usr/share/pear/$_gitname/gitty.php"

_binpath="$pkgdir/usr/bin"
_binsh="$pkgdir/usr/bin/gitty"

build() {

	cd "$srcdir"
	
	msg "Remove existing download git src"
	rm -rf "$_gitname"

	msg "Connecting to GIT server...."
	git clone $_gitroot $_gitname

	msg "GIT checkout done or server timeout"
	msg "Starting Make..."

	cd "$srcdir/$_gitname"

	rm -rf "$_installto"

	mkdir -p $_installto

	cp -R $srcdir/$_gitname/* "$_installto"

	rm -rf "$_binsh"

	mkdir -p "$_binpath"

	touch "$_binsh"

	echo "#/bin/sh" > "$_binsh"
	echo php $_phpscript '"$1" "$2" "$3" "$4"' >> "$_binsh"

	chmod +x "$_binsh"

	chmod -R 777 "$_installto"

}
