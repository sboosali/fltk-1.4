# 

## Installation

```
wget https://github.com/fltk/fltk/archive/master.tar.gz
tar xvf master.tar.gz
cd fltk-master/

sudo apt-get install -y freeglut3-dev

make configure
./configure --enable-gl --enable-shared --enable-localjpeg --enable-localzlib --enable-localpng --enable-xft 
make
sudo make install
```

`freeglut3-dev` installs:

  freeglut3 libdrm-dev libgl1-mesa-dev libglu1-mesa-dev libice-dev libsm-dev libx11-xcb-dev
  libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev
  libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxdamage-dev
  libxfixes-dev libxshmfence-dev libxt-dev libxxf86vm-dev mesa-common-dev x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-xf86vidmode-dev

register:

```
# NO:
# $ cp -rav fltk-master/ ~/haskell/fltkhs/

# YES:
$ sudo make install
```

## Errors

###

   $ make
   /usr/bin/ld: Fl_Adjuster.o: relocation R_X86_64_32S against `_ZTV11Fl_Valuator' can not be used when making a shared object; recompile with -fPIC

### 

```
# if `--with-pic` isn't recognized:

make clean
./configure CFLAGS=-fPIC CXXFLAGS=-fPIC --enable-shared ...
```

i.e.:

```
./configure CFLAGS="-fPIC" CXXFLAGS="-fPIC" --enable-shared --enable-gl --with-x --enable-localjpeg --enable-localzlib --enable-localpng --enable-xft
```

## Notes: `./configure --help`

```help
$ ./configure --help
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking ...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR            user executables [EPREFIX/bin]
  --sbindir=DIR           system admin executables [EPREFIX/sbin]
  --libexecdir=DIR        program executables [EPREFIX/libexec]
  --sysconfdir=DIR        read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data [PREFIX/var]
  --runstatedir=DIR       modifiable per-process data [LOCALSTATEDIR/run]
  --libdir=DIR            object code libraries [EPREFIX/lib]
  --includedir=DIR        C header files [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc [/usr/include]
  --datarootdir=DIR       read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR           read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR           info documentation [DATAROOTDIR/info]
  --localedir=DIR         locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR            man documentation [DATAROOTDIR/man]
  --docdir=DIR            documentation root [DATAROOTDIR/doc/PACKAGE]
  --htmldir=DIR           html documentation [DOCDIR]
  --dvidir=DIR            dvi documentation [DOCDIR]
  --pdfdir=DIR            pdf documentation [DOCDIR]
  --psdir=DIR             ps documentation [DOCDIR]

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]

Optional Features:
  --disable-option-checking  ignore unrecognized --enable/--with options
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-cygwin         use the Cygwin libraries [default=no]
  --enable-x11            with Cygwin or Mac OS, use X11 [default=no]
  --enable-cairoext       use fltk code instrumentation for cairo extended use [default=no]
  --enable-cairo          use lib Cairo [default=no]
  --enable-debug          turn on debugging [default=no]
  --enable-cp936          turn on CP936 [default=no]
  --enable-gl             turn on OpenGL support [default=yes]
  --enable-shared         turn on shared libraries [default=no]
  --enable-threads        enable multi-threading support [default=yes]
  --disable-largefile     omit support for large files
  --enable-localzlib      use local ZLIB library [default=auto]
  --enable-localpng       use local PNG library  [default=auto]
  --enable-localjpeg      use local JPEG library [default=auto]
  --enable-nanosvg        use nanosvg to support SVG images  [default=yes]
  --enable-print          turn on print support (X11 platform) [default=yes]
  --enable-xinerama       turn on Xinerama support [default=yes]
  --enable-xft            turn on Xft support [default=yes]
  --enable-pango          turn on Pango support [default=no]
  --enable-xdbe           turn on Xdbe support [default=yes]
  --enable-xfixes         turn on Xfixes support [default=yes]
  --enable-xcursor        turn on Xcursor support [default=yes]
  --enable-xrender        turn on Xrender support [default=yes]

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-abiversion       Build with FL_ABI_VERSION, e.g. 10304 for FLTK 1.3.4
  --with-optim="flags"    use custom optimization flags
  --with-archflags="flags"
			  use custom architecture flags
			  (possible Mac OS X values include -arch i386, -arch x86_64, -arch ppc)
  --with-links            make header links for common misspellings [default=no]
  --with-x                use the X Window System

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  LIBS        libraries to pass to the linker, e.g. -l<library>
  CPPFLAGS    (Objective) C/C++ preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CPP         C preprocessor
  XMKMF       Path to xmkmf, Makefile generator for X Window System

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to the package provider.
```

## `fltk-config`

```
$ fltk-config --ldflags
-L/nix/store/xnx5gv9mjrl7dny01kfc0jjygayzzfyb-fltk-1.3.4/lib -Wl,-rpath,/nix/store/xnx5gv9mjrl7dny01kfc0jjygayzzfyb-fltk-1.3.4/lib -lfltk -lXrender -lXfixes -lXext -lXft -lfontconfig -lpthread -ldl -lm -lX11

$ fltk-config --ldstaticflags
/nix/store/xnx5gv9mjrl7dny01kfc0jjygayzzfyb-fltk-1.3.4/lib/libfltk.a -lXrender -lXfixes -lXext -lXft -lfontconfig -lpthread -ldl -lm -lX11

```
