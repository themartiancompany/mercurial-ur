# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Giovanni Scafora <linuxmania@gmail.com>
# Contributor: David 'SleepyDog' <goodluv@gmail.com>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgname=mercurial
pkgver=1.3.1
pkgrel=2
pkgdesc="A scalable distributed SCM tool"
url="http://www.selenic.com/mercurial"
arch=('i686' 'x86_64')
license=('GPL')
depends=('python>=2.6' 'tk')
source=(http://www.selenic.com/mercurial/release/$pkgname-$pkgver.tar.gz)
md5sums=('6504f0dc32bd7ecf59a9f7f719432e76')

build() {
    cd $srcdir/$pkgname-$pkgver
    python setup.py install --root $pkgdir || return 1

    install -d $pkgdir/usr/share/man/{man1,man5}
    install -m644 doc/hg.1 $pkgdir/usr/share/man/man1 || return 1
    install -m644 doc/{hgrc.5,hgignore.5} $pkgdir/usr/share/man/man5 || return 1
    install -m755 contrib/hgk $pkgdir/usr/bin || return 1
    install -m644 -D contrib/zsh_completion $pkgdir/usr/share/zsh/site-functions/_hg || return 1
    install -m644 -D contrib/bash_completion $pkgdir/etc/bash_completion.d/hg || return 1
    install -d $pkgdir/usr/share/emacs/site-lisp
    install -m644 contrib/{mq.el,mercurial.el} $pkgdir/usr/share/emacs/site-lisp || return 1
     
    vimpath="$pkgdir/usr/share/vim"
    install -m644 -D contrib/vim/HGAnnotate.vim $vimpath/syntax/HGAnnotate.vim || return 1
}
