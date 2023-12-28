The directories contain the build directories of quictls, nghttp3, ngtcp2, and curl as they were at build time. 
You'll need to build perl/host as a dependency of libcurl, but it will fail in Alpine Linux unless if you use the build command `PERL5LIB=/{root_dir}/openwrt/staging_dir/hostpkg/usr/lib/perl5/5.38.2/ make`. However, if you need to use perl packages from host, copy the files from /usr/lib/perl5/core_perl inside the Alpine Linux host into $(PERL5LIB) directory to make sure everything's there. Symlinks don't work, at least from root to workdir. Please do not use the binary .ipk files, they are only there as proof of build. Follow the guide here: https://openwrt.org/docs/guide-developer/toolchain/use-buildsystem

After customizing through `make menuconfig` use these commands to build the packages:

make package/libs/openssl/compile && \
mkdir -p staging_dir/hostpkg/usr/lib/perl5/5.38.2 && \
cp -r /usr/lib/perl5/core_perl/* staging_dir/hostpkg/usr/lib/perl5/5.38.2/ && \
PERL5LIB=/workdir/openwrt/staging_dir/hostpkg/usr/lib/perl5/5.38.2/ make package/feeds/packages/perl/compile && \
make package/feeds/packages/nghttp2/compile && make ~/openwrt/package/feeds/packages/nghttp3/compile && \
make ~/openwrt/package/feeds/packages/ngtcp2/compile && \
make ~/openwrt/package/feeds/packages/curl/compile

Do another `make` and, if there are no issues with your selection of packages, everything should compile successfully.
