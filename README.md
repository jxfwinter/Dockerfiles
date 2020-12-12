# Dockerfiles
c/c++开发镜像与centos8基础运行镜像:  
1 可ssh连接,root默认密码rt20dev88  
2 可支持容器内挂载windows共享文件夹  
  
c7-dev目录：  
centos7系统,包含默认的gcc4.8 gdb版本，详细可查看Dockerfile文件   
  
启动容器命令：  
docker pull jxfwinter/env:c7-dev  
docker run --restart always -d --name c7-dev-gcc48 --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /etc/localtime:/etc/localtime:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 jxfwinter/env:c7-dev  
  
