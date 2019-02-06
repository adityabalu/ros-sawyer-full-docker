bootstrap: docker
From: docker://kailiang/ros-sawyer-full-nvidia:Init
%labels

AUTHOR Aditya Balu baditya@iastate.edu

%environment
    CPATH="/usr/local/cuda/include:$CPATH"
    PATH="/usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}"
    LD_LIBRARY_PATH="/usr/local/nvidia/lib:/usr/local/nvidia/lib64:/usr/local/cuda/lib64:${LD_LIBRARY_PATH}"
    CUDA_HOME="/usr/local/cuda"
    NVIDIA_VISIBLE_DEVICES=all
    NVIDIA_DRIVER_CAPABILITIES=compute,utility
    NVIDIA_REQUIRE_CUDA="cuda>=9.0"
    export PATH LD_LIBRARY_PATH CPATH CUDA_HOME

%post
    . /environment
    # use bash as default shell
    echo "\n #Using bash as default shell \n" >> /environment
    echo 'SHELL=/bin/bash' >> /environment

    # default mount paths
    mkdir /scratch /data 

    #Add CUDA paths
    echo "\n #Cuda paths \n" >> /environment
    echo 'export CPATH="/usr/local/cuda/include:$CPATH"' >> /environment
    echo 'export PATH="/usr/local/cuda/bin:$PATH"' >> /environment
    echo 'export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"' >> /environment
    echo 'export CUDA_HOME="/usr/local/cuda"' >> /environment
    echo "/usr/local/cuda-9.0/lib64/" >/etc/ld.so.conf.d/cuda.conf
    echo "/usr/local/cuda/extras/CUPTI/lib64/" >>/etc/ld.so.conf.d/cuda.conf
    echo "/usr/local/nvidia/lib" >> /etc/ld.so.conf.d/nvidia.conf
    echo "/usr/local/nvidia/lib64" >> /etc/ld.so.conf.d/nvidia.conf
