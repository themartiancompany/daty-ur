# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2023, 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_proj="gnome"
_pkg="Daty"
pkgname=daty
pkgver="1.0beta"
_commit="fe03fd9f5f5ed63b79f22731159c911c33beab69"
pkgrel=1
pkgdesc='Daty Wikidata Editor'
_http="https://gitlab.${_proj}.org"
_ns="World"
url="${_http}/${_ns}/${_pkg}"
license=(
  'AGPLv3'
)
arch=(
  'aarch64'
  'arm'
  'armv7l'
  'i686'
  'mips'
  'pentium4'
  'powerpc'
  'x86_64'
)
depends=(
  'libhandy0'
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-appdirs"
  "${_py}-bleach"
  "${_py}-beautifulsoup4"
  "${_py}-gobject"
  "${_py}-requests"
  "${_py}-setproctitle"
  "${_py}-pywikibot"
)
makedepends=(
  # 'git'
  "${_py}-setuptools"
)
provides=(
  "${_py}-${pkgname}=${pkgver}"
)
conflicts=(
  "${_py}-${pkgname}"
)
groups=(
  "${_proj}-extra"
)
if [[ "${_git}" == "false" ]]; then
  _tag_name="tag"
  _tag="${pkgver}"
elif [[ "${_git}" == "true" ]]; then
  _tag_name="commit"
  _tag="${_commit}"
fi
_tarname="${_pkg}-${_tag}"
if [[ "${_git}" == "false" ]]; then
  _uri="${url}/-/archive/${pkgver}/${_pkg}-${pkgver}.tar.gz"
  _src="${_tarname}.tar.gz::${_uri}"
  _sha512_sum='4d2aae19b217d0a568c9ba0cfbe1df61fb2695bdec20f7ac4a8fccb9ea97bc8aa9135070c35835736371c880cea2621abb02c9ca2944d455bb66de1c777b4b61'
  sha512sums=(
    "${_sha512_sum}"
  )
elif [[ "${_git}" == "true" ]]; then
  _uri="git+${url}#${_tag_name}=${_tag}"
  _src="${_tarname}::${_uri}"
  _sum="SKIP"
fi
source=(
  "${_src}"
)

# shellcheck disable=SC2154
package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    "setup.py" \
    install \
    --root="${pkgdir}" \
    --optimize=1
}

# vim:set sw=2 sts=-1 et:
