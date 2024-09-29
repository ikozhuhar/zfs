### Файловая система ZFS

#### <a name='toc'>Содержание</a>
1. [Определение алгоритма с наилучшим сжатием](#compression)
2. [Определение настроек пула](#pool_settings)
3. [Работа со снапшотом](#snapshots)
4. [Рекомендуемые источники](#recommended_sources)

#### 1. [[⬆]](#toc) <a name='compression'>Определение алгоритма с наилучшим сжатием</a>

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

##### Скачиваем один и тот же текстовый файл во все пулы:
![image](https://github.com/user-attachments/assets/511e1f28-894e-4377-82b1-8247761a6030)

##### Проверим, что файл был скачан во все пулы:
![image](https://github.com/user-attachments/assets/70155d6a-eed8-4d00-9e8c-733cc6cb05ce)

##### Проверим, сколько места занимает один и тот же файл в разных пулах и проверим степень сжатия файлов `zfs list`:
![image](https://github.com/user-attachments/assets/09d31f3f-ac99-4c74-965f-49040c58f50f)

##### Таким образом, у нас получается, что алгоритм gzip-9 самый эффективный по сжатию. 
![image](https://github.com/user-attachments/assets/d1e44a66-3e4f-473f-8f12-27f62ae7cb45)


#### 2. [[⬆]](#toc) <a name='pool_settings'>Определение настроек пула</a>

##### Скачиваем архив в домашний каталог и разархивируем его:
![image](https://github.com/user-attachments/assets/f7cdf191-f27b-4bde-9c22-7874d1950f59)

##### Проверим, возможно ли импортировать данный каталог в пул.
![image](https://github.com/user-attachments/assets/0208aa91-400d-4f99-855b-12f4fdc7bd51)

##### Команда `zpool status` выдаст нам информацию о составе импортированного пула.
![image](https://github.com/user-attachments/assets/56f5938d-c165-4e01-a57d-ebdf71a1f017)

##### Далее нам нужно определить настройки командами: `zpool get all otus` и `zfs get all otus`
![image](https://github.com/user-attachments/assets/d6dc80c6-4b19-4764-9363-6df67489a104)

##### C помощью фильтра grep можно уточнить конкретный параметр, например:
![image](https://github.com/user-attachments/assets/c011fa30-6dda-4f29-83b8-2880557e9823)


#### 3. [[⬆]](#toc) <a name='snapshots'>Работа со снапшотом, поиск сообщения</a>

##### Скачаем файл
![image](https://github.com/user-attachments/assets/b7c6ccf8-6394-4cab-b5de-25e5241e2e2b)

##### Восстановим файловую систему из снапшота:
![image](https://github.com/user-attachments/assets/db5603b4-6a38-4950-81e2-1c664fae2480)

##### Ищем в каталоге /otus/test файл с именем “secret_message”:
![image](https://github.com/user-attachments/assets/9a6e177e-e640-45e8-8787-5e6a037e4d6a)

##### Смотрим содержимое найденного файла:
![image](https://github.com/user-attachments/assets/ae69979e-2e17-4cb2-b8d5-71b0a7bb66e8)


#### 4. [[⬆]](#toc) <a name='recommended_sources'>Рекомендуемые источники</a>

[Статья о ZFS](https://ru.wikipedia.org/wiki/ZFS)

[Статья «Что такое ZFS? И почему люди от неё без ума?»](https://habr.com/ru/articles/424651/)

[Официальная документация по Oracle Solaris ZFS](https://docs.oracle.com/cd/E19253-01/819-5461/gbcya/index.html)

[Статья о ZFS (теория и практика)](http://xgu.ru/wiki/ZFS)







