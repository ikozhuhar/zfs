### Файловая система ZFS

#### 1. Определение алгоритма с наилучшим сжатием

##### Смотрим список всех дисков, которые есть в виртуальной машине: `lsblk`
![image](https://github.com/user-attachments/assets/c2d27d37-a182-4ef0-8105-b2d43056856f)

##### Создаём 4 пула из двух дисков в режиме RAID 1:
![image](https://github.com/user-attachments/assets/072f5c4b-0d9b-46f3-abbf-3b68c9ed2b39)

##### Смотрим информацию о пулах: `zpool list` и `zpool status`
![image](https://github.com/user-attachments/assets/097a261c-4189-4021-b178-e3ff7088585d)

##### Добавляем разные алгоритмы сжатия в каждую файловую систему (`lzjb, lz4, gzip-9, zle`):
![image](https://github.com/user-attachments/assets/ae914ebd-3cb7-4964-9f91-47c7870278b2)

##### Проверим, что все файловые системы имеют разные методы сжатия:
![image](https://github.com/user-attachments/assets/ffa50488-dcec-41df-a424-80cf9180eebb)





