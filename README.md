# nginx
原理 负载均衡 高并发解决
  1.nginx是高性能的http服务器/反向代理服务器
  
  2.功能作用:
    作集群:减轻服务器的压力
    作反向代理服务器:不暴露真实的ip地址
    作虚拟服务器:
    动静分离服务器:
    (安全架构需要解决那些问题:不暴露真实的ip地址 使用https防止http抓包 系统黑白名单 sql注入 模拟请求csrf(攻击业务) 跨站脚本攻击XSS 
    流量攻击ddos(大量请求，占用宽带))
    
   3. 反向代理服务器有：Nginx、lvs、F5（硬件）、haproxy
   
   4.在windows和linux安装配置是一样的
   
   5.负载均衡策略
          1、轮询（默认）
          每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。 
          upstream backserver { 
          server 192.168.0.14; 
          server 192.168.0.15; 
          } 

          2、指定权重
          指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。 
          upstream backserver { 
          server 192.168.0.14 weight=10; 
          server 192.168.0.15 weight=10; 
          } 

          3、IP绑定 ip_hash
          每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决session的问题。 
          upstream backserver { 
          ip_hash; 
          server 192.168.0.14:88; 
          server 192.168.0.15:80; 
          } 
          4、fair（第三方）
          按后端服务器的响应时间来分配请求，响应时间短的优先分配。 
          upstream backserver { 
          server server1; 
          server server2; 
          fair; 
          } 
          5、url_hash（第三方）
          按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，后端服务器为缓存时比较有效。 
          upstream backserver { 
          server squid1:3128; 
          server squid2:3128; 
          hash $request_uri; 
          hash_method crc32; 
          } 
   
   6.看doc文档
