# perl
##Byteloader 模块安装

    perl -MCPAN -e shell
    cpan>install Byteloader
    #报错
    The most recent version "1.35" of the module "ExtUtils::Embed" is part of the perl-5.28.1 distribution. 
    To install that, you need to run   force install ExtUtils::Embed   --or--   install S/SH/SHAY/perl-5.28.1.tar.gz
    #解决
    yum install perl-ExtUtils-Embed
    #问题
    RURBAN/B-C-1.55.tar.gz : make_test NO
    #解决
    cpan>install B::CC
    #报错
    同上
    #解决（源码安装）
    wget https://cpan.metacpan.org/authors/id/R/RU/RURBAN/B-C-1.55.tar.gz
    tar -xzf B-C-1.55.tar.gz
    cd B-C-1.55
    perl Makefile.PL
    make
    make test
    make install

