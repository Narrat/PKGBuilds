# Maintainer: Lex Black <autumn-wind at web dot de>
# Contributor: Michael Jakl <jakl.michael@gmail.com>
# With contributions from many kind people at https://aur.archlinux.org/packages/julia-git/

_pkgbase=julia
pkgbase=${_pkgbase}-git
pkgname=(julia-git julia-git-docs)
pkgver=1.6.0.DEV.r47019.g8db94953f2c
pkgrel=1
arch=(x86_64)
pkgdesc='High-level, high-performance, dynamic programming language'
url='https://julialang.org/'
license=(MIT)
depends=(cblas hicolor-icon-theme libgit2 libunwind libutf8proc openblas
         libssh2 lapack curl gmp 
         suitesparse mbedtls mpfr openlibm pcre2
         xdg-utils desktop-file-utils 
         gtk-update-icon-cache)
makedepends=(cmake gcc-fortran python git)
source=(git+https://github.com/JuliaLang/julia.git#branch=master
        Make.user
        julia-system-cblas.patch
        libunwind-version.patch
        make-install-no-build.patch)
sha256sums=('SKIP'
            '1aee33d62dcd8e6b65672bd9996a61c83e44056dd31efa79761cb85effb0e6a1'
            'd4c8fe9eec1bc416549924ae328ceb3f63cc736ecd5e67886faa924e7c14bc5d'
            '856dab2da8124df95e4fbd17f1164bebe1b10e99852fedf38f9dfe31f8ae295c'
            '0b57e0bc6e25c92fde8a6474394f7a99bfb57f9b5d0f7b53f988622ae67de8b7')


pkgver() {
  cd $_pkgbase

  # use the version from VERSION file
  ver=`git show makepkg:VERSION | sed 's/-/./g'`
  # Combine ver with rev-count and latest commit
  printf "%s.r%s.g%s" $(echo $ver) "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd $_pkgbase
  git submodule init
  git submodule update

  msg2 'Configuring the build...'
  cp -v $srcdir/Make.user .

  # Add and use option to build with system cblas
  patch -p1 -i ../julia-system-cblas.patch

  # Fixing libunwind version check
  # https://github.com/JuliaLang/julia/pull/29082
  patch -p1 -i ../libunwind-version.patch

  # Don't build again in install
  patch -p1 -i ../make-install-no-build.patch
}

build() {
  # See FS#57387 for why USE_SYSTEM_LLVM=0 is used, for now
  # See FS#58221 for why USE_SYSTEM_ARPACK=0 is used, for now
  export PATH="$srcdir/bin:$PATH"
  env CFLAGS="$CFLAGS -w" CXXFLAGS="$CXXFLAGS -w" make VERBOSE=1 -C "$_pkgbase"

  # Building doc
  cd $_pkgbase/doc
  make
}

check() {
  cd "$_pkgbase/test"

  # this is the make testall target, plus the --skip option from
  # travis/appveyor/circleci (one test fails with DNS resolution errors)
  ../julia --check-bounds=yes --startup-file=no ./runtests.jl all --skip Sockets --skip Distributed --skip LibGit2/libgit2
  find ../stdlib \( -name \*.cov -o -name \*.mem \) -delete
  rm -r depot/compiled
}

package_julia-git() {
  optdepends=('openblas-lapack: multithreaded replacement for lapack'
              'fftw: If using the FFTW package from julia'
              'gnuplot: If using the Gaston Package from julia')
  provides=('julia')
  conflicts=('julia')
  backup=(etc/julia/startup.jl)


  make -C "$_pkgbase" DESTDIR="$pkgdir" install \
    prefix=/usr \
    libexecdir=/usr/lib \
    sysconfdir=/etc

  # Documentation is in the julia-git-docs package.
  # Man pages in /usr/share/julia/doc/man are duplicate.
  rm -rf "$pkgdir/usr/share/"{doc,julia/doc,icons/hicolor/scalable}

  # Install icons
  for i in 16 32 128 256 512
  do
    mkdir -p $pkgdir/usr/share/icons/hicolor/${i}x${i}
    install -Dm644 $srcdir/julia/contrib/mac/frameworkapp/JuliaLauncher/Assets.xcassets/AppIcon.appiconset/$i.png $pkgdir/usr/share/icons/hicolor/${i}x${i}/apps/${i}x${i}.png
  done

  # Install licence
  install -Dm644 "$_pkgbase/LICENSE.md" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.md"

  # Rm files that don't belong into the package
  find ${pkgdir} -name ".gitignore" -delete
}

package_julia-git-docs() {
  arch=('any')
  pkgdesc='Documentation and examples for Julia'
  depends=(julia)
  provides=(julia-docs)
  conflicts=(julia-docs julia-git-doc)

  install -d "$pkgdir/usr/share/doc"
  cp -r "$_pkgbase/doc" "$pkgdir/usr/share/doc/$_pkgbase"
  rm -rf "$pkgdir/usr/share/doc/julia/man"
  install -Dm644 "$_pkgbase/LICENSE.md" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.md"

  # Installing built docs; adj accord to changes in build()
  cd "$_pkgbase/doc/_build"
  cp -dpr --no-preserve=ownership html $pkgdir/usr/share/doc/julia/

  # Fix symlinks that point to the build directory
  for i in $(ls -lR $pkgdir | grep "^l" | grep "src/julia" | cut -d '>' -f 1 | rev | cut -d ' ' -f 2 | rev)
  do
    I=$(find $pkgdir -name "$i")
    L=$(ls -ld $I)
    syml=$(echo $L | rev | cut -d '>' -f 2 | rev | sed 's/.*pkg\/julia\-git\-docs//g' | sed 's/ -//g')
    symd=$(echo $L | rev | cut -d '>' -f 1 | rev | sed 's/.*julia-git\/src\/julia//g')
    ln -sf $symd $pkgdir/$syml
  done

  # Rm duplicate/unused files
  rm -rf $pkgdir/usr/share/doc/julia/{build,_build,deps,src}
  rm $pkgdir/usr/share/doc/julia/{make.jl,Makefile,Manifest.toml,NEWS-update.jl,Project.toml,README.md,UnicodeData.txt}
  # Rm files that don't belong in the package
  find ${pkgdir} -name ".gitignore" -delete
}
