build deps:
sudo dnf install git ninja-build clang cmake python uuid uuid-devel libicu libicu-devel libbsd libbsd-devel libedit libedit-devel libxml2 libxml2-devel sqlite sqlite-devel swig python-devel ncurses ncurses-devel pkgconfig libcurl libcurl-devel autoconf libtool systemtap systemtap-sdt-devel
careful:
- clang >= 3.6
- cmake >= 3.5.2



This step is important, as the update-checkout script will utilize Swift's parent directory in order to checkout all the dependencies

mkdir swift-source
cd swift-source

git clone https://github.com/apple/swift.git
./swift/utils/update-checkout --clone

build:
utils/build-script -r -t
