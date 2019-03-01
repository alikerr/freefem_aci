BootStrap: shub
From: shub://willgpaik/centos7_aci:latest
%setup

%files

%environment 
    PATH="$PATH:/opt/sw/freefem/bin"
    export PATH

%runscript


%post
    yum -y install m4-devel \
      bison-devel \
      flex-devel \
      patch \
      openmpi-devel \
      fftw-devel \
      openblas-devel \
      lapack-devel
    yum -y update

    source /opt/rh/devtoolset-8/enable

    # Install FreeFem++
    mkdir -p /opt/sw/
    cd /opt/
    wget https://raw.githubusercontent.com/willgpaik/freefem_aci/master/freefem_install.sh
    chmod +x freefem_install.sh
    ./freefem_install.sh
    
    rm freefem_install.sh
