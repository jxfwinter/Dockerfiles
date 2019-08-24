# Dockerfiles
centos7 c/c++ 开发镜像:  
1 可ssh连接,root默认密码rt20dev88  
2 可支持容器内挂载windows共享文件夹  
3 支持systemd  
  
centos7-dev目录：  
包含系统默认的gcc gdb版本，详细可查看Dockerfile文件  

centos7-dev-dtool8目录：  
包含scl中的gcc8 gdb8版本，详细可查看Dockerfile文件  
  
启动容器命令：  
docker run -d --name dtool8-dev --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 centos7-dev:default  

docker run -d --name dtool8-dev --cap-add SYS_ADMIN --cap-add DAC_READ_SEARCH -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 2200:22 centos7-dev:dtool8  
