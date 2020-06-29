# Virtual-Jewelry-Tryon-Platform-TryOn-Module

基于Android的虚拟饰品试穿平台，试穿模块部分

## 前言
由于前期设计及和后期实现的差别问题，将饰品定义为能够在面部穿戴的物品，包括但不限于耳环，帽子眼镜等物品。测试数据中目前只存在帽子和眼镜种类。


## 准备
试穿模块需要通过nginx，web服务器进行反向代理供客户端访问使用，本模块基于[jeeliz/jeelizFaceFilter](https://github.com/jeeliz/jeelizFaceFilter) 进行开发。

由于模块需要https协议进行访问，所以需要将nginx的配置增加https的配置，打开防火墙等操作。
```
mv ./nginx.conf /etc/nginx/nginx.conf
```

同时需要更改nginx.conf的文件位置以及生成ssl
```
        ssl_certificate "/etc/nginx/conf.d/server.crt";
        ssl_certificate_key "/etc/nginx/conf.d/server.key";
```

打开防火墙对应的接口
```
firewall-cmd --zone=public --add-port=443/tcp --permanent
firewall-cmd --reload
```

## 运行
将项目放在/usr/share/nginx/html里面后启动nginx
```
nginx
```