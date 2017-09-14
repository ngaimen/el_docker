DOCKER入门知识， 以及自用dockerfile              

**1. 安装**              
$ apt-get install docker.io

启动服务和守护进程           

$ service docker.io status

$ service docker.io start

创建软连接            

ln -sf /usr/bin/docker.io /usr/local/bin/docker


**2. 搜索可用镜像**      
sudo docker search ubuntu


**3. 下载镜像**      
sudo docker pull ubuntu:14.04

**4. 查看镜像**          
sudo docker images

**5. 启动**       
sudo docker run -it ca38f2eac26b /bin/bash        

带宿主机目录启动         
sudo docker run -it -v [宿主机目录](eg:~/download):[容器机目录](eg:/home/hello) 镜像 /bin/bash             

退出时自动删除容器                
sudo docker run --rm -it -v [宿主机目录](eg:~/download):[容器机目录](eg:/home/hello) 镜像 /bin/bash        

**6. 编译镜像**        
sudo docker build -t ubuntu:myaosp . 
