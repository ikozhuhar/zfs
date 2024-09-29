#### Файловая система ZFS

##### 1. Определение алгоритма с наилучшим сжатием

###### Смотрим список всех дисков, которые есть в виртуальной машине: `lsblk`

![image](https://github.com/user-attachments/assets/3fef23c0-1d8a-4893-9f82-ee07dca900b4)

###### Создаём 4 пула из двух дисков в режиме RAID 1:
![image](https://github.com/user-attachments/assets/93d65914-572b-4657-96a5-124c207ca31b)

###### Смотрим информацию о пулах: `zpool list`



