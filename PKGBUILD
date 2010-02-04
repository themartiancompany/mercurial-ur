# Maintainer: Giovanni Scafora <giovanni@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgname=mercurial
pkgver=1.4.3
pkgrel=1
pkgdesc="A scalable distributed SCM tool"
arch=('i686' 'x86_64')
url="http://www.selenic.com/mercurial"
license=('GPL')
depends=('python>=2.6')
optdepends=('tk: for the hgk GUI')
source=(http://www.selenic.com/mercurial/release/${pkgname}-${pkgver}.tar.gz)
md5sums=('b075a2a6a08c10405ef3483aecb1a991')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  python setup.py install --root="${pkgdir}/" --optimize=1 || return 1

  install -d ${pkgdir}/usr/share/man/{man1,man5}
  install -m644 doc/hg.1 "${pkgdir}/usr/share/man/man1" || return 1
  install -m644 doc/{hgrc.5,hgignore.5} "${pkgdir}/usr/share/man/man5" || return 1
  install -m755 contrib/hgk "${pkgdir}/usr/bin" || return 1
  install -m644 -D contrib/zsh_completion "${pkgdir}/usr/share/zsh/site-functions/_hg" || return 1
  install -m644 -D contrib/bash_completion "${pkgdir}/etc/bash_completion.d/hg" || return 1
  install -d "${pkgdir}/usr/share/emacs/site-lisp"
  install -m644 contrib/{mq.el,mercurial.el} "${pkgdir}/usr/share/emacs/site-lisp" || return 1

  vimpath="${pkgdir}/usr/share/vim/vimfiles"
  install -Dm644 contrib/vim/HGAnnotate.vim "${vimpath}/syntax/HGAnnotate.vim" || return 1
}
