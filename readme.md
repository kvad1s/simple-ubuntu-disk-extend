# Simple Ubuntu storage extension
> Easiest way to expand your Ubuntu VM Storage Size.

## General Information
- Ubuntu use LVM for default to storing data and after expanding your VM size in VMWare/Hyper-V/KVM your discs does not size automatically. For this we need to extend our partition with free additional space and expand LVM.

## 1) Expand virtual disk of your VM
./screenshot

## 2) Login in your VM using SSH (or any diffrent method) and after login execute
`sudo su`

## 3) Rescan your storage device (in your case can be used sdb/sdc etc.)
`echo 1 > /sys/class/block/sda/device/rescan`

## 4) Install growpart which part of cloud-utils-package
`sudo apt install -y cloud-utils`

## 5) Use growpart to enlarge partition to maximum size 
`growpart /dev/sda 3`

where '/dev/sda' your storage device, '3' - used partition

## 6) Resize ext4 file system 
`resize2fs /dev/sda3`

## 7) Extend ubuntu-vg LVM group 
`sudo vgextend ubuntu-vg /dev/vdb`

Thanks for attention! 