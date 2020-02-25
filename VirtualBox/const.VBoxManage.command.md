### 常用命令 VBoxMange


> 介绍：<br />
> 1.虚拟机VirtualBox的管理命令VBoxMange<br />
>下面的使用安利 centos 作为虚拟主机名称,centos.os 代表系统镜像名称,centos.vdi 虚拟磁盘<br />

```
#创建一个空虚拟主机
VBoxManage createvm --name centos --register

#创建5124M的硬盘镜像
VBoxManage createhd --filename centos --size 5124

#添加host-only网卡vboxnet0
VBoxManage hostonlyif create

#设置系统名称为centos
VBoxManage modifyvm centos --ostype centos

#设置系统内存分配512M
VBoxManage modifyvm centos --memory 512

#虚拟硬件挂载，镜像载入，网卡配置
VBoxManage storagectl centos --name IDE --add ide --controller PIIX4 --bootable on

VBoxManage storagectl centos --name SATA --add sata --controller IntelAhci --bootable on

VBoxManage storageattach centos --storagectl SATA --port 0 --device 0 --type hdd --medium "/centos.vdi"

VBoxManage storageattach centos --storagectl IDE --port 0 --device 0 --type dvddrive --medium centos.os

VBoxManage modifyvm centos --nic1 nat --nictype1 82540EM --cableconnected1 on

VBoxManage modifyvm centos --nic2 nat --nictype2 82540EM --cableconnected2 on

VBoxManage modifyvm centos --vram 128 --accelerate3d on --audio alsa --audiocontroller ac97

#虚拟主机详情
VBoxManage showvminfo centos

#虚拟主机服务器开启
VBoxManage startvm centos --type headless

#关闭虚拟主机
VBoxManage controlvm centos poweroff

#拷贝现有的系统盘
VBoxManage clonevdi   "centos.vdi" "centos-new.vdi"
```
