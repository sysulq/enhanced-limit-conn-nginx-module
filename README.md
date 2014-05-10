Enhanced-limit-conn-nginx-module
================================

This is an enhanced limit conn nginx module with sysguard ability.

##Feature

1. Combined sysguard module from Tengine.
2. Enable to configure in main block.
3. No bad effect on the origin limit conn function.
4. Totally compatible with Nginx.

##Notice
1. Replace ngx_http_limit_conn_module with ngx_http_enhanced_limit_conn_module directly.
2. Without sysguard on, this module will act the same as ngx_http_limit_conn_module.
3. With sysguard on, this module will limit connections unless this system running nginx is overload.

##Configuration

```
limit_conn_zone $binary_remote_addr zone=addr:10m;
limit_conn addr 50;

sysguard on;
sysguard_load load=8;
sysguard_mem swapratio=20%;
sysguard_mem free=100M;
```

##Directives

###limit_conn_zone
同limit_conn模块一致

###limit_conn
同limit_conn模块一致

###sysguard
**syntax**: sysguard on | off

**default**: sysguard on

**context**: http, server, location, location if

开始系统状态监控功能，当超过所设置的阀值，则将limit_conn的限制连接数减半，以应对HTTP DOS攻击。

###sysguard_load
**syntax**: sysguard_load load=[0-10];

**default**: sysguard_load load=8

**context**: http, server, location, location if

设置系统CPU负载阀值

###sysguard_mem
**syntax**: sysguard_mem swapratio=[0-100]%;
        sysguard_mem free=[0-1000]M;

**default**: sysguard_mem swapratio=20%;
         sysguard_mem free=100M;

**context**: http, server, location, location if

设置系统内存阀值

##Contact me
Email: hnlq.sysu@gmail.com
