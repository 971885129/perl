# perl
##Byteloader 模块安装
* 搜索perl module ： https://metacpan.org/


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
        #报错
        #尝试另一方法
        cpanm ByteLoader
        #报错
        ! Installing the dependencies failed: Module 'B::Flags' is not installed, Module 'Opcodes' is not installed
        ! Bailing out the installation for B-C-1.55.
        #解决
        cpanm B::Flags
        #问题
        cpanm会显示安装成功，但用perldoc -l Opcodes去检测Opcodes模块却检测不到，去/usr/lib64/perl5/目录下可以看到，Opcodes.pm出现在/usr/lib64/perl5/lib/perl5/x86_64-linux-thread-multi/目录下，将其移到/usr/lib64/perl5/下，并修改权限即可检测到。
        可能模块调用位置与安装位置不一致。
        ##解决
        * 最终发现原因为root用户安装module路径和perl调用module路径不一致。
        * 解决方法
                * root 默认安装在/root/perl5/lib/perl5/目录下
                * 环境变量中增加该目录
        #问题
        * 普通用户无法访问root所安装的模块

    


