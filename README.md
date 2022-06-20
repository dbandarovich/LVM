1. Создать 4 файла размером 1Гб каждый, создать loopback устройства из файлов при помощи losetup. :
    ```sh
    sudo dd if=/dev/zero of=./file1 bs=1G count=1
    sudo dd if=/dev/zero of=./file2 bs=1G count=1
    sudo dd if=/dev/zero of=./file3 bs=1G count=1
    sudo dd if=/dev/zero of=./file4 bs=1G count=1
    ```
    <p align="left">
    <a href="https://github.com/dbandarovich/LVM/blob/main/images/files.PNG">
      <img src="images/files.PNG">
    </a>
    <p align="left">
  
    <p align="left">
    <a href="https://github.com/DmitryBond/WorkWithKubernetes/blob/main/images/losetup.png">
      <img src="images/losetup.png">
    </a>
    <p align="left">
2. Создать физические разделы на этих устройствах при помощи pvcreate. Создать volume group из первых двух девайсов. На ней создать logical volume при помощи lvcreate. 
    ```sh
    sudo pvcreate /dev/loop15
    sudo pvcreate /dev/loop16
    sudo pvcreate /dev/loop17
    sudo pvcreate /dev/loop18
    ```
    <p align="left">
    <a href="https://github.com/DmitryBond/WorkWithKubernetes/blob/main/images/new_volumes.png">
      <img src="images/new_volumes.png">
    </a>
    <p align="left">   
      
    ```sh
    sudo vgcreate vg01 /dev/loop15 /dev/loop16 
    ```
        
    <p align="left">
    <a href="https://github.com/DmitryBond/WorkWithKubernetes/blob/main/images/group01.png>
      <img src="images/group01.png">
    </a>
    <p align="left"> 
                   
    ```sh
    sudo lvcreate -L 1.99G -n first_v vg01 
    ```
                                  
      
