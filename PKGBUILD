#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors
# FixMe: Add code to clean JavaScript code. see https://wiki.archlinux.org/title/Node.js_package_guidelines

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

pkgname="jsdoc"
pkgver=3.6.10
pkgrel=1
pkgdesc="An API documentation generator for JavaScript"
url="https://github.com/jsdoc3/$pkgname"
arch=("any")
license=("APACHE")
depends=("nodejs")
makedepends=("npm")
source=("https://registry.npmjs.org/$pkgname/-/$pkgname-$pkgver.tgz")
sha512sums=("21d43ca694a8e4b299f68dccf8b28820af22d340c87b99ac0ef1b71bcd4a9bed5d872d17ace583d098bc1fad44960c848ff3bd2912e892029b00cf575fd08902")

build() {
	cd "$srcdir/package"
	npm --cache "$srcdir/npm-cache" install
	npm pack
}

package() {
	npm install -g --cache "$srcdir/npm-cache" --prefix "$pkgdir/usr" "$srcdir/package/jsdoc-$pkgver.tgz"
	chown -R root:root "$pkgdir/"*
}
