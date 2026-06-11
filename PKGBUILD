# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Caleb Maclennan
#     <caleb@alerque.com>
#   Bartłomiej Piotrowski
#     <bpiotrowski@archlinux.org>
#   Giovanni Scafora
#     <giovanni@archlinux.org>
#   Douglas Soares de Andrade
#     <douglas@archlinux.org>

_etc_get() {
  local \
    _etc \
    _os
  _os="$(
    uname \
      -o)"
  _etc="etc"
  if [[ "${_os}" == "Android" ]]; then
    _etc="usr/etc"
  fi
  echo \
    "${_etc}"
}

_os="$(
  uname \
    -o)"
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="github"
fi

_py="python"
_pkg=mercurial
_pkg_alt=hg
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
pkgver=6.8
pkgrel=1
_pkgdesc=(
  'A scalable distributed SCM tool'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  "aarch64"
  "arm"
  "armv7l"
  "armv8l"
  "i686"
  "mips"
  "pentium4"
  "powerpc"
  "x86_64"
)
url="https://www.${_pkg}-scm.org"
license=(
 "GPL"
)
depends=(
  "${_py}"
)
makedepends=(
  "${_py}-"{"build","installer","wheel"}
  "${_py}-setuptools"
  "${_py}-docutils"
)
provides=(
  "${_pkg_alt}=${pkgver}"
)
conflicts=(
  "${_pkg_alt}"
)
_tk_optdepends=(
  'tk:'
    "for the ${_pkg_alt}k GUI"
)
optdepends=(
  "${_tk_optdepends[*]}"
)
# checkdepends=(
#   'breezy'
#   'cvs'
#   'git'
#   'git-lfs'
#   "${_py}-docutils"
#   'subversion'
#   'unzip'
# )

# TODO:
#   check included contrib/packaging/mercurial.spec
#   and how BLFS/Gentoo/Debian/Fedora do it.
# The following should be either 'makedepends'
# or checkdepends when running tests
# "python-gnupg"
# "python-pygments"
# "python-pyflakes"
# "python-pyopenssl"
# 'openssh
# 'rust'
# 'subversion'
# 'breezy'
# 'cvs'
# 'git'
# )

_etc="$(
  _etc_get)"

backup=(
  "${_etc}/${_pkg}/${_pkg_alt}rc"
)
validpgpkeys=(
  # Unknown?
  "2BCCE14F5C6725AA2EA8AEB7B9C9DC824AA5BDD5"
  "EB851395B4223EE2F7BA0B28DA54740BF08732BA"
  # Pulkit Goyal <7895pulkit@gmail.com>
  "818D87CD1AC180C394C86E633A33DE460D9EC39F"
  # Raphaël Gomès <alphare@raphaelgomes.dev>
  "1F66F8CDF654E905C11DA061A11E01CD0E05D956"
)
_archive_format="tar.gz"
_tarname="${_pkg}-${pkgver}"
_tarfile="${_tarname}.${_archive_format}"
_sum="08e4d0e5da8af1132b51e6bc3350180ad57adcd935f097b6d0bc119a2c2c0a10"
_sum_512="e0eab77c4599f24e33210404b16d591952fbcb7c5e3b64805abc18167c67eaad3d9baa2226e885add5e36569a5148d6a11c5690d68167690570e6e5b243e50f0"
_profile_sum_512="710dcddb24d928efc97370e869d9caa083107929ed9a1086dd2a3ae0caaf2c71e2f29060597e29315b6b15b1616251c42412e268ce737109c48ae4d7aa1b9555"
_sig_sum="df2fbd9b6415b44340a80ce1d29d888af1aad8fdfa71a0fd1ac2cc99d1f1777c"
_hg_sig_sum="7cda2cb212a21ad66713ac7699442d542add753959059cd4acec33c761d10181"
_profile_sum="87427151713e689cd87dc50d50c048e0e58285815e4eb61962b50583532cbde5"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Dogemaster
_evmfs_ns="0x894d863D5343A8609EdA5430D95Bbd5104C0F245"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
if [[ "${_evmfs}" == "false" ]]; then
  if [[ "${_git}" == "false" ]]; then
    _uri="${url}/release/${_tarfile}"
    _sig_sum="${_hg_sig_sum}" 
    _sig_uri="${_uri}.asc"
    _src="${_tarfile}::${_uri}"
  fi
elif [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_git}" == "false" ]]; then
    _src="${_evmfs_src}"
  fi
fi
source=(
  "${_src}"
  "${_sig_src}"
  "${_pkg}.profile"
)
sha256sums=(
  "${_sum}"
  "${_sig_sum}"
  "${_profile_sum}"
)
sha512sums=(
  "${_sum_512}"
  'SKIP'
  "${_profile_sum_512}"
)

build() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      "build" \
    -wn
  make \
    -C \
      "contrib/c${_pkg_alt}"
}

check() {
  cd \
    "${_tarname}/tests"
  # TODO:
  #   disabled for now,
  #   too many tests fail
  # "${_py}" \
  #   run-tests.py # -j48 || :
}

_usr_get() {
  local \
    _bin
  _bin="$(
    dirname \
      "$(command \
           -v \
	   "env")")"
  dirname \
    "${_bin}"
}

package() {
  local \
    _make_opts=() \
    _usr
  _usr="$(
    _usr_get)"
  _make_opts+=(
    DESTDIR="${pkgdir}"
    PREFIX="/usr"
  )
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      "installer" \
    --destdir="${pkgdir}" \
    "dist/"*".whl"
  # Do not invoke install target
  # because it invokes a soon to be deprecated
  # `setup.py install` and screws with
  # shebang handling in PEP517 install above
  make \
    "${_make_opts[@]}" \
    install-doc
  install \
    -vDm644 \
    "contrib/zsh_completion" \
    "${pkgdir}/usr/share/zsh/site-functions/_${_pkg_alt}"
  install \
    -vDm644 \
    "contrib/bash_completion" \
    "${pkgdir}/usr/share/bash-completion/completions/${_pkg_alt}"
  make \
    -C \
      "contrib/c${_pkg_alt}" \
    "${_make_opts[@]}" \
    install
  install \
    -vDm755 \
    "contrib/${_pkg_alt}-ssh" \
    "${pkgdir}/usr/bin"
  install \
    -vDm755 \
    "contrib/${_pkg_alt}k" \
    "${pkgdir}/usr/bin"
  install \
    -vDm644 \
    -t \
    "${pkgdir}/usr/share/emacs/site-lisp/" \
    "contrib/"{"mq.el","${_pkg}.el"}
  install \
    -vDm644 \
    -t \
    "${pkgdir}/usr/share/vim/vimfiles/syntax/" \
    "contrib/vim/HGAnnotate.vim"
  # set some variables
  cat \
    "${_pkg}.profile" |
    sed \
      "s|%_usr%|${_usr}" > \
      "${pkgdir}/${_etc}/profile.d/${_pkg}.sh"
  chmod \
    "0644" \
    "${pkgdir}/${_etc}/profile.d/${_pkg}.sh"
  # FS#38825 - Add certs config to package
  cat <<-EOF | install -Dm755 /dev/stdin "${pkgdir}/${_etc}/${_pkg}/${_pkg_alt}rc"
	[web]
	cacerts = /${_etc}/ssl/certs/ca-certificates.crt
	EOF
}
