# pgrpms

yum install perl bison flex readline-devel zlib-devel
yum install rpm-build

wget https://download.postgresql.org/pub/repos/yum/common/redhat/rhel-8.2-x86_64/pgdg-srpm-macros-1.0.22-1.rhel8.noarch.rpm
rpm -ivh pgdg-srpm-macros-1.0.22-1.rhel8.noarch.rpm
wget http://mirror.centos.org/centos/8/PowerTools/x86_64/os/Packages/opensp-1.5.2-28.el8.x86_64.rpm
rpm -ivh opensp-1.5.2-28.el8.x86_64.rpm

mkdir rpmbuild
mkdir -pv rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}

chmod u+x configure
tar --exclude='postgresql-12.1/.git' -jcf postgresql-12.1.tar.bz2 postgresql-12.1
cp postgresql-12.1.tar.bz2 rpmbuild/SOURCES/

cd rpmbuild/SOURCES
wget https://www.postgresql.org/files/documentation/pdf/12/postgresql-12-A4.pdf
rpmbuild -bb postgresql-10.spec