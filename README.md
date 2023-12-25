The directories contain the build directories of quictls, nghttp3, ngtcp2, and curl as they were at build time. 
For curl the build command used was `PERL5LIB=/{root_dir}/openwrt/staging_dir/hostpkg/usr/lib/perl5/5.38.2/ make`.
Also, all files from /usr/lib/perl5/core_perl inside the Alpine Linux host were copied into $(PERL5LIB) directory to 
make sure everything's there. Please do not use the binary .ipk file, they are only there as proof of build.
