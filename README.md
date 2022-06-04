#### The dmsetup command is a command line wrapper for communication with the Device Mapper. For general system information about LVM devices

```
[root@ip-172-31-26-233 ~]# dmsetup info
Name:              vg00-lv_files
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        0
Event number:      0
Major, minor:      253, 1
Number of targets: 1
UUID: LVM-8d84NTNyqDOT0bmRHdHmEhT141sgnLr3WTj4tbWcaQv7IBYJqaCEDecB3RbZX5At

Name:              vg00-lv_project
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        0
Event number:      0
Major, minor:      253, 0
Number of targets: 1
UUID: LVM-8d84NTNyqDOT0bmRHdHmEhT141sgnLr3ZtUbzvF0L8DAgOdinEcHKc8YGXqImkQi
```

#### You can list the device names of mapped devices with the dmsetup ls command

```

[root@ip-172-31-26-233 ~]# dmsetup ls
vg00-lv_files	(253:1)
vg00-lv_project	(253:0)
```


#### The vgs command provides volume group information in a configurable form, displaying one line per volume group.

```
[root@ip-172-31-26-233 ~]# vgs
  VG   #PV #LV #SN Attr   VSize  VFree  
  vg00   1   2   0 wz--n- <2.00g 520.00m
```
  
#### The vgdisplay command displays volume group properties (such as size, extents, number of physical volumes, and so on) in a fixed form.
#### [ -v|--verbose ]
  
```
[root@ip-172-31-26-233 ~]# vgdisplay -v vg00
  --- Volume group ---
  VG Name               vg00
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <2.00 GiB
  PE Size               4.00 MiB
  Total PE              511
  Alloc PE / Size       381 / <1.49 GiB
  Free  PE / Size       130 / 520.00 MiB
  VG UUID               8d84NT-NyqD-OT0b-mRHd-HmEh-T141-sgnLr3
   
  --- Logical volume ---
  LV Path                /dev/vg00/lv_project
  LV Name                lv_project
  VG Name                vg00
  LV UUID                ZtUbzv-F0L8-DAgO-dinE-cHKc-8YGX-qImkQi
  LV Write Access        read/write
  LV Creation host, time ip-172-31-26-233.ec2.internal, 2022-06-03 06:17:58 +0000
  LV Status              available
  # open                 1
  LV Size                1.00 GiB
  Current LE             256
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/vg00/lv_files
  LV Name                lv_files
  VG Name                vg00
  LV UUID                WTj4tb-WcaQ-v7IB-YJqa-CEDe-cB3R-bZX5At
  LV Write Access        read/write
  LV Creation host, time ip-172-31-26-233.ec2.internal, 2022-06-03 06:18:21 +0000
  LV Status              available
  # open                 1
  LV Size                500.00 MiB
  Current LE             125
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Physical volumes ---
  PV Name               /dev/sdb1     
  PV UUID               gDzmVo-9EVb-mY3z-sEJP-615A-dyXL-QhtFR1
  PV Status             allocatable
  Total PE / Free PE    511 / 130

 ```
  
 #### The lvs command provides logical volume information in a configurable form, displaying one line per logical volume. 
 
 ``` 
[root@ip-172-31-26-233 ~]# lvs -a -o +devices
  LV         VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert Devices       
  lv_files   vg00 -wi-ao---- 500.00m                                                     /dev/sdb1(256)
  lv_project vg00 -wi-ao----   1.00g                                                     /dev/sdb1(0

```


| Option  | Desciption|
---------|-----------
-a       | --all
-o       | --options
--devices| Devices that the command can use
+        | will append the specified fields to the default fields


              
              
