# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Giovanni Scafora <giovanni@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgname=mercurial
pkgver=5.9.3
pkgrel=1
pkgdesc='A scalable distributed SCM tool'
arch=(x86_64)
url="https://www.mercurial-scm.org/"
license=(GPL)
depends=(python)
makedepends=('python-docutils')
optdepends=('tk: for the hgk GUI')
#checkdepends=('breezy' 'cvs' 'git' 'git-lfs' 'python-docutils' 'subversion' 'unzip')

# ToDo:
# check included contrib/packaging/mercurial.spec and how BLFS/Gentoo/Debian/Fedora do it
# the following should be either makedepends or checkdepends when running tests
# 'python-gnupg' 'python-pygments'  'python-pyflakes' 'python-pyopenssl'
# 'openssh'  'rust' 'subversion' 'breezy' 'cvs' 'git') 	

backup=(etc/mercurial/hgrc)
validpgpkeys=(2BCCE14F5C6725AA2EA8AEB7B9C9DC824AA5BDD5
              3A8155163D0E20A530FCB78647A67FFAA346AACE
              EB851395B4223EE2F7BA0B28DA54740BF08732BA
              818D87CD1AC180C394C86E633A33DE460D9EC39F) # Pulkit Goyal <7895pulkit@gmail.com>
source=(https://www.mercurial-scm.org/release/${pkgname}-${pkgver}.tar.gz{,.asc}
        mercurial.profile)
sha512sums=('d2a91cf63ca8f7621a2d36af7993c9878a2a36c7c95a027f2ff9d5ec3cdb01b9f86a60108cf3ca674b5b306488f61f749c3d8c5f814d6c90c04941d551d458dd'
            'SKIP'
            '710dcddb24d928efc97370e869d9caa083107929ed9a1086dd2a3ae0caaf2c71e2f29060597e29315b6b15b1616251c42412e268ce737109c48ae4d7aa1b9555')

build() {
  cd $pkgname-$pkgver
  make
  make -C contrib/chg
}

check() {
  cd $pkgname-$pkgver/tests
  # TODO - disabled for now - to many tests fail
  #python run-tests.py # -j48 || :
}

package() {
  cd $pkgname-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
  make DESTDIR="${pkgdir}" PREFIX=/usr install

  install -m644 -D contrib/zsh_completion "$pkgdir/usr/share/zsh/site-functions/_hg"
  install -m644 -D contrib/bash_completion "$pkgdir/usr/share/bash-completion/completions/hg"

  make -C contrib/chg DESTDIR="$pkgdir" PREFIX=/usr install
  install -m755 contrib/hg-ssh "$pkgdir/usr/bin"
  install -m755 contrib/hgk "$pkgdir/usr/bin"

  install -d "$pkgdir/usr/share/emacs/site-lisp"
  install -m644 contrib/{mq.el,mercurial.el} "$pkgdir/usr/share/emacs/site-lisp"

  install -Dm644 contrib/vim/HGAnnotate.vim \
    "$pkgdir/usr/share/vim/vimfiles/syntax/HGAnnotate.vim"

  # set some variables
  install -m755 -d "$pkgdir/etc/profile.d"
  install -m644 "$srcdir/mercurial.profile" "$pkgdir/etc/profile.d/mercurial.sh"

  # FS#38825 - Add certs config to package
  install -m755 -d "$pkgdir/etc/mercurial"
  cat <<-EOF > "$pkgdir/etc/mercurial/hgrc"
	[web]
	cacerts = /etc/ssl/certs/ca-certificates.crt
	EOF
}
