# Обновление ядра базовой системы
1) Загрузил версию ядра 4.17
```
wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.17.11.tar.xz
```
2) Распаковал
```
tar -xvf linux-4.17.11.tar.xz
```
3) Настроил ядро с использованием следующих параметров конфигурации в среде CentOS 7
```
CONFIG_KVM_GUEST=y
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_PCI_LEGACY=y
CONFIG_BLK_DEV_SD=y
CONFIG_SCSI_VIRTIO=y
CONFIG_VIRTIO_NET=y
CONFIG_SERIAL_8250=y
CONFIG_SERIAL_8250_CONSOLE=y
```
4) Скопировал текущую конфигурацию ядра (.config) из каталога /boot в новый каталог linux-4.17.11
```
cp -v /boot/config-3.10.0-1160.81.1.el7.x86_64 /usr/src/linux-4.17.11/.config
```
5) Запустил команду make menuconfig, чтобы настроить ядро ​Linux
```
cd /usr/src/linux-4.17.11/
make menuconfig
```

6) Скомпилировал и установил ядро ​​и модули, используя следующие команды
```
make bzImage
make modules
make
make install
make modules_install
```

7) Перезапустился
```
reboot
```