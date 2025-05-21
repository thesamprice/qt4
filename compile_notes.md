wget http://ftp.gnu.org/gnu/gcc/gcc-7.5.0/gcc-7.5.0.tar.gz
tar -xzf gcc-7.5.0.tar.gz
cd gcc-7.5.0
./contrib/download_prerequisites

mkdir build && cd build
../configure --prefix=/opt/gcc-7.5.0 --enable-languages=c,c++ --disable-multilib --disable-libsanitizer
make -j$(nproc)
sudo make install

export PATH=/opt/gcc-7.5.0/bin:$PATH


export CC=/opt/gcc-7.5.0/bin/gcc
export CXX=/opt/gcc-7.5.0/bin/g++

./configure -prefix /opt/qt4.8.6 \
    -opensource -confirm-license -release -fast \
    -nomake examples -nomake demos \
    -no-phonon -no-webkit \
    -qt-zlib -qt-libjpeg -qt-libpng -no-openssl  -no-qt3support -no-webkit -fast -no-javascript-jit

make -j$(nproc)
sudo make install