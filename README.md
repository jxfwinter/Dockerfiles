# Dockerfiles
c/c++开发镜像与centos8基础运行镜像:  
1 可ssh连接,root默认密码rt20dev88  
2 可支持容器内挂载windows共享文件夹  
3 支持systemd  

c7-dev目录：  
centos7系统,包含默认的gcc4.8 gdb版本，详细可查看Dockerfile文件   

c8-dev目录：  
centos8系统,包含默认的gcc8 gdb8版本，详细可查看Dockerfile文件  

c8-base-run目录：  
centos8系统,基础运行环境镜像，可在此基础上构建自己的服务运行镜像,详细可查看Dockerfile文件  

u1904-dev目录：  
ubuntu1904系统,包含默认的gcc版本，详细可查看Dockerfile文件  
  
启动容器命令：  
docker pull jxfwinter/env:c7-dev  
docker run --restart always -d --name c7-dev-gcc48 --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /etc/localtime:/etc/localtime:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 jxfwinter/dev-env:env:c7-dev  

docker pull jxfwinter/dev-env:c8-dev  
docker run --restart always -d --name c8-dev-gcc8 --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /etc/localtime:/etc/localtime:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 jxfwinter/dev-env:c8-dev  
