# Maintainer: Joost Bremmer <toost.b@gmail.com>
# Contributor: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: olantwin <olantwin@gmail.com>

pkgbase=neovim-airline
pkgname=('neovim-airline' 'neovim-airline-themes')
arch=('any')
license=('MIT')
makedepends=('git')
groups=('neovim-plugins')

#temp pkgver variables
pkgver=1.0
pkgrel=1
_main_pkgver=0.8
_themes_pkgver=r1146.5a6453c
source=("${pkgname[0]}::git://github.com/vim-airline/${pkgname[0]#neo}.git#tag=v$_main_pkgver"
        "${pkgname[1]}::git://github.com/vim-airline/${pkgname[1]#neo}.git#commit=${_themes_pkgver#*.}")
sha256sums=('SKIP' 'SKIP')

# Neovim install dir
_installpath="usr/share/nvim/runtime"

package_neovim-airline() {
  # set package local variables
  pkgver=$_main_pkgver
  pkgrel=1
  pkgdesc='Lean & mean statusline/tabline for Neovim'
  url='https://github.com/vim-airline/vim-airline'
  depends=('neovim' 'neovim-airline-themes')
  install='nvim-doc.install'

  cd "${pkgname[0]}"
  install -Dvm755 doc/airline.txt "$pkgdir/$_installpath/doc/airline.txt"
  install -Dvm755 plugin/airline.vim "$pkgdir/$_installpath/plugin/airline.vim"
  install -dv "$pkgdir/$_installpath/autoload"
  install -dv "$pkgdir/$_installpath/t"
  cp -R autoload/* "$pkgdir/$_installpath/autoload"
  cp -R t/* "$pkgdir/$_installpath/t"
  install -Dvm644 LICENSE "$pkgdir/usr/share/licenses/${pkgname[0]}/LICENSE"

  # This one conflicts with vim-airline-themes
  rm "$pkgdir/usr/share/nvim/runtime/autoload/airline/themes/dark.vim"
}

package_neovim-airline-themes(){
  # set package local variables
  pkgver=$_themes_pkgver
  pkgrel=1
  pkgdesc='Themes for neovim-airline'
  depends=('neovim-airline')

  cd "${pkgname[1]}"
  install -dv "$pkgdir/$_installpath"
  cp -r --no-preserve=owner autoload plugin "$pkgdir/$_installpath"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/${pkgname[1]}/LICENSE"
}

# getver: raw.githubusercontent.com/vim-airline/vim-airline/master/CHANGELOG.md
# vim:set ts=2 sw=2 et:
