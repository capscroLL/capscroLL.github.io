---
title: Ubuntu 18.04 更改主机名
---

# Ubuntu 18.04 更改主机名

```shell
sudo vi /etc/hostname
sudo vi /etc/cloud/cloud.cfg
将 preserve_hostname: false 修改为 true
sudo reboot
```