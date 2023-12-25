The directories contain the build directories of quictls, nghttp3, ngtcp2, and curl as they were at build time. 
~~For curl the build command used was `PERL5LIB=/{root_dir}/openwrt/staging_dir/hostpkg/usr/lib/perl5/5.38.2/ make`.~~
I decided to add the library definition into the perl Makefile - it's fully automatic, and curl will build without issue.
However, all files from /usr/lib/perl5/core_perl inside the Alpine Linux host still need to be copied into $(PERL5LIB) directory to 
make sure everything's there. Symlinks don't work, at least from root to workdir. Please do not use the binary .ipk files, they are only there as proof of build.
