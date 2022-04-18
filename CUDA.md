DELL windows转Ubuntu
1. F2进入bios
2. general-boot sequence设置启动盘顺序
3. system configuration–sata operation设置AHCI
  (AHCI 为Ubuntu，Raidon为Windows)
4. Secure boot-Secure boot enable关掉
  （若ubuntu转Windows则打开）


装linux
0. 打开disk genius，分配240g空闲

[操作，数据类型，大小，卷标]
1. 新建主磁盘分区 fat32 2g 卷标efi
2. 新建主磁盘分区 linux swap 20g
3. 新建扩展分区
4. 新建逻辑分区 ext4 35g 卷标/
5. 新建逻辑分区 ext4 剩余全部 卷标/home


装显卡驱动和cuda
1. 打开软件和更新 附加驱动 选470（ubuntu18.04）


装cudnn
1. 登录https://developer.nvidia.com/zh-cn/cudnn
2. 填问卷，下载对应版本cudnn即可
