> Metrics server 项目地址

    https://github.com/kubernetes-sigs/metrics-server

> 下载弟子

    wget https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.5.0/components.yaml

> 修改文件

   spec:
         containers:
           - args:
           - --cert-dir=/tmp
           - --secure-port=443
           - --kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname
           - --kubelet-use-node-status-port
           - --kubelet-insecure-tls  //增加一条，不验证kubelet提供的https证书
           - --metric-resolution=15s
           image: k8s.gcr.io/metrics-server/metrics-server:v0.5.0


> 或是使用一下部署方式

   下载components.yaml：git clone https://github.com/hzqcuriosty/metrics-server.git

   修改components.yaml 镜像为huochaoying/metrics-server:v0.3.7或huochaoying/metrics-server:v0.4.1

   进入metrics-server目录： 执行 kubectl apply -f components.yaml
