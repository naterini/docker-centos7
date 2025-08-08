FROM centos:7
#All the offical Centos7 repos are dead and need to be purged
RUN rm -Rf /etc/yum.repos.d/*.repo
#Switch to vault repos for Centos7
COPY centos7.repo /etc/yum.repos.d/
RUN yum update -y
# yum update adds back all the repos which need to be purged again
RUN find /etc/yum.repos.d/ -name \*.repo ! -name centos7.repo | \
	xargs -i unlink {}
# Disable gpg checks as keys are expired or not already retrieved
RUN find /etc/yum.repos.d/ -name \*.repo | \
	xargs -i sed 's/^gpgcheck=.*$/gpgcheck=0/g' -i {}
RUN yum -y install --exclude google-chrome-* \
	rpm gcc automake make perl-macros rpm-build \
	readline-devel openssl-devel openssl pam-devel \
	perl-ExtUtils-MakeMaker.noarch mariadb-devel mariadb \
	glib2-devel gtk2-devel libtool git vim \
	perl-Switch expect lua-devel rrdtool-devel lz4-devel json-c-devel \
	libcurl-devel freeipmi-devel numactl-devel lynx numactl \
	rdma-core-devel gcc-c++ flex libgcrypt-devel gcc-gfortran \
	strace ltrace wget cmake sudo jansson-devel \
	openssh-server pam-devel xterm \
	xauth man mailx postfix http-parser-devel \
	libyaml-devel mlocate gettext-devel texinfo \
	systemd python3 \
	iproute pdsh msmtp \
	rsync gpgme-devel libseccomp-devel \
	libassuan-devel dbus-devel bash-completion \
	libevent-devel hwloc-devel \
	hdf5-devel openmpi3 munge munge-devel libjwt-devel
