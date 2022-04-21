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

```shell
ip link
```
La interfaz tiene que estar `UP`

```shell
ip a
```
Comprobamos que tenemos una dirección asignada

```shell
ping -c 1 archlinux.org
```
Comprobamos que podemos hacer `ping`

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

