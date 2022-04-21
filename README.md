# Arch-Linux VM
## Descarga la ISO de ArchLinux
https://archlinux.org/download/

## Crea una nueva máquina virtual
* Selecciona la ISO de ArchLinux
* Selecciona Debian como tipo de SO
* Selecciona UEFI como tipo de firmware (con BIOS la configuración cambia ligeramente)
* Configura la máquina virtual

## Iniciamos la máquina virtual
* Selecciona el modo de instalación

## Configuramos Arch Linux
* Cambiamos el idioma del teclado

```shell
loadkeys es
```

* Comprobamos que tenemos conexión
La interfaz tiene que estar `UP`

```shell
ip link
```
Comprobamos que tenemos una dirección asignada

```shell
ip a
```
Comprobamos que podemos hacer `ping`

```shell
ping -c 1 archlinux.org
```

* Actualizamos la hora del sistema

```shell
timedatectl set-ntp true
```

* Configuramos los discos

```shell
fdisk -l
```
Localizamos el disco en el que instalaremos Arch Linux (si solo hemos puesto un disco sera `/dev/sda`)

```shell
fdisk /dev/sda
```
|  Particion  | Tamaño |  Tipo de particion |
| ----------- | ------ | ------------------ |
| `/dev/sda1` |  512M  | EFI (FAT-12/16/32) |
| `/dev/sda2` |   4G   |    Linux swap      |
| `/dev/sda3` | 15.5G  |       Linux        |

Formateamos las particiones

```shell
mkfs.fat -F 32 /dev/sda1
mkswap /dev/sda2
mkfs.ext4 /dev/sda3
```
Montamos las particiones

```shell
mount /dev/sda3 /mnt
mount --mkdir /dev/sda1 /mnt/boot
swapon /dev/sda2
```

* Instalamos los paquetes esenciales
