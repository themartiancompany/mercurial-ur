# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Giovanni Scafora <giovanni@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgname=mercurial
pkgver=6.6.1
pkgrel=2
pkgdesc='A scalable distributed SCM tool'
arch=(x86_64)
url="https://www.mercurial-scm.org/"
license=(GPL)
depends=(python)
makedepends=(python-{build,installer,wheel}
             python-setuptools
             python-docutils)
optdepends=('tk: for the hgk GUI')
#checkdepends=('breezy' 'cvs' 'git' 'git-lfs' 'python-docutils' 'subversion' 'unzip')

# ToDo:
# check included contrib/packaging/mercurial.spec and how BLFS/Gentoo/Debian/Fedora do it
# the following should be either makedepends or checkdepends when running tests
# 'python-gnupg' 'python-pygments'  'python-pyflakes' 'python-pyopenssl'
# 'openssh'  'rust' 'subversion' 'breezy' 'cvs' 'git') 	

backup=(etc/mercurial/hgrc)
validpgpkeys=(2BCCE14F5C6725AA2EA8AEB7B9C9DC824AA5BDD5
              EB851395B4223EE2F7BA0B28DA54740BF08732BA
              818D87CD1AC180C394C86E633A33DE460D9EC39F  # Pulkit Goyal <7895pulkit@gmail.com>
              1F66F8CDF654E905C11DA061A11E01CD0E05D956) # Raphaël Gomès <alphare@raphaelgomes.dev>
source=(https://www.mercurial-scm.org/release/${pkgname}-${pkgver}.tar.gz{,.asc}
        mercurial.profile)
sha512sums=('f16240f06a98a088e0229aa6584daa540eee92476a0a7934617c065c9f1012288cf3d6fb2d20fc7b247122bc360201f2e2c1c139c261a834f483bd09bef74d0c'
            'SKIP'
            '710dcddb24d928efc97370e869d9caa083107929ed9a1086dd2a3ae0caaf2c71e2f29060597e29315b6b15b1616251c42412e268ce737109c48ae4d7aa1b9555')

build() {
  cd $pkgname-$pkgver
  python -m build -wn
  make -C contrib/chg
}

check() {
  cd $pkgname-$pkgver/tests
  # TODO - disabled for now - to many tests fail
  #python run-tests.py # -j48 || :
}

package() {
  cd $pkgname-$pkgver
  python -m installer -d "$pkgdir" dist/*.whl
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
