BootStrap: shub
From: shub://willgpaik/centos7_aci:latest
%setup

%files

%environment 
    PATH="$PATH:/usr/lib64/openmpi/bin/:/opt/sw/freefem/bin/"
    export PATH
    LD_PRELOAD="/opt/eod/lib/libopentextdlfaker.so.3:/opt/eod/lib/libopentextglfaker.so.3 \
        :/opt/eod/lib64/libopentextdlfaker.so.3:/opt/eod/lib64/libopentextglfaker.so.3"
    export LD_PRELOAD

%runscript


%post
    yum -y install m4-devel \
      bison-devel \
      flex-devel \
      patch \
      openmpi-devel \
      fftw-devel \
      openblas-devel \
      lapack-devel \
      freeglut-devel \
      scotch-devel \
      arpack-devel \
      suitesparse-devel \
      MUMPS-devel \
      NLopt-devel \
      coin-or-Ipopt-devel \
      gnuplot \
      superLU-devel \
      hypre \
      perl-Digest-MD5
    yum -y update

    source /opt/rh/devtoolset-8/enable

    # Install FreeFem++
    mkdir -p /opt/sw/
    cd /opt/
    wget https://raw.githubusercontent.com/willgpaik/freefem_aci/master/freefem_install.sh
    chmod +x freefem_install.sh
    ./freefem_install.sh
    
    rm freefem_install.sh
    
    # Download requires libraries for EoD:
    cd /opt/
    svn export https://github.com/willgpaik/MorphoGraphX_aci.git/trunk/eod_graphics_libraries
    mv eod_graphics_libraries eod
