enhanced-limit-conn-nginx-module
================================

This is an enhanced limit conn nginx module.

###Feature

1. Combined sysguard module from Tengine.
2. Enable to configure in main block.
3. No bad effect on the origin limit conn function.

###Configuration

```
limit_conn_zone $binary_remote_addr zone=addr:10m;
limit_conn addr 50;

sysguard on;
sysguard_load load=8;
sysguard_mem swapratio=20%;
sysguard_mem free=100M;
```

###Contact me
Emal: hnlq.sysu@gmail.com
