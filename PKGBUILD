# Contributor: Jeff Mickey <jeff@archlinux.org>
# Contributor: Giovanni Scafora <linuxmania@gmail.com>
# Contributor: David 'SleepyDog' <goodluv@gmail.com>
# Maintainer: Douglas Soares de Andrade <douglas@archlinux.org>

pkgname=mercurial
pkgver=1.3
pkgrel=3
pkgdesc="A scalable distributed SCM tool"
url="http://www.selenic.com/mercurial"
license=("GPL")
depends=('python>=2.6')
source=(http://www.selenic.com/mercurial/release/$pkgname-$pkgver.tar.gz)
arch=('i686' 'x86_64')

build() {
    cd $srcdir/$pkgname-$pkgver
    python setup.py install --root $pkgdir

    install -d $pkgdir/usr/share/man/{man1,man5}
    install -m644 doc/hg.1 $pkgdir/usr/share/man/man1
    install -m644 doc/{hgrc.5,hgignore.5} $pkgdir/usr/share/man/man5
    install -m755 contrib/hgk $pkgdir/usr/bin
    install -m644 -D contrib/zsh_completion $pkgdir/usr/share/zsh/site-functions/_hg
    install -m644 -D contrib/bash_completion $pkgdir/etc/bash_completion.d/hg 
    install -d $pkgdir/usr/share/emacs/site-lisp
    install -m644 contrib/{mq.el,mercurial.el} $pkgdir/usr/share/emacs/site-lisp
     
    vimpath="$pkgdir/usr/share/vim"
    install -m644 -D contrib/vim/HGAnnotate.vim $vimpath/syntax/HGAnnotate.vim
}
md5sums=('d25a867e0ef835faafdbe1e82e239945')
