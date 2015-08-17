# Maintainer: James McGlashan (archeyDevil)
#   <james.mcglashan@affinityvision.com.au>

pkgname=omz-archey-git
pkgver=20120430
pkgrel=1
pkgdesc="A handful of functions, auto-complete helpers, and stuff that makes you shout. Note, this is a fork of the official oh-my-zsh, the main goal was to get a system-wide patch, however improved lots more."
arch=('any')
url="http://github.com/archeydevil/oh-my-zsh"
license=('unknown')
depends=('zsh>=4.3.9')
makedepends=('git')
optdepends=('python' 'curl' 'git' 'pkgtools' 'python-pygments')
install='omz.install'
conflicts=('grml-zsh-config')

# Cleaner _git format
_gitdomain='github.com'
_gituser='archeydevil'
_gitname='oh-my-zsh'
_gitbranch='master' # (master/sorin)
_gitroot="https://$_gitdomain/$_gituser/$_gitname.git"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server.... [$_gitdomain:$_gituser:$_gitname:$_gitbranch]"
  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    git checkout $_gitbranch
    msg "The local files are updated."
  else
    git clone --depth=0 $_gitroot $_gitname --branch $_gitbranch
  fi
  msg "GIT checkout done or server timeout"
}

package() {
  install -d "$pkgdir/usr/share/oh-my-zsh"
  cp -a oh-my-zsh/* "$pkgdir/usr/share/oh-my-zsh"

  mkdir -p "$pkgdir/usr/share/zsh/site-functions"
  cp "$pkgdir/usr/share/oh-my-zsh/omz" "$pkgdir/usr/share/zsh/site-functions/"
}

# vim:set ts=2 sw=2 et:
