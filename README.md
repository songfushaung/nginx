# nginx
原理 负载均衡 高并发解决
  1.nginx是高性能的http服务器/反向代理服务器
  2.功能:
    作集群:减轻服务器的压力
    作反向代理:不暴露真实的ip地址
    作虚拟服务器:
    动静分离服务器:
    (安全架构需要解决那些问题:不暴露真实的ip地址 使用https防止http抓包 系统黑白名单 sql注入 模拟请求csrf(攻击业务) 跨站脚本攻击XSS 
    流量攻击ddos(大量请求，占用宽带))
   3. 反向代理服务器有：Nginx、lvs、F5（硬件）、haproxy
    
