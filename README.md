# Dockerfiles
c/c++ 开发镜像:  
1 可ssh连接,root默认密码rt20dev88  
2 可支持容器内挂载windows共享文件夹  
3 支持systemd  
  
c7-gcc48目录：  
centos7系统,包含默认的gcc gdb版本，详细可查看Dockerfile文件  

c7-gcc82目录：  
centos7系统,包含scl中的gcc8 gdb8版本，详细可查看Dockerfile文件  

c8-gcc8目录：  
centos8系统,包含默认的gcc8 gdb8版本，详细可查看Dockerfile文件  

u1904-dev目录：  
ubuntu1904系统,包含默认的gcc版本，详细可查看Dockerfile文件  
  
启动容器命令：
docker pull jxfwinter/dev-env:c7-gcc48  
docker run --restart always -d --name c7-dev-g48 --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /etc/localtime:/etc/localtime:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 jxfwinter/dev-env:c7-gcc48  

docker pull jxfwinter/dev-env:c8-gcc8  
docker run --restart always -d --name c8-dev-gcc8 --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /etc/localtime:/etc/localtime:ro -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 jxfwinter/dev-env:c8-gcc8   
