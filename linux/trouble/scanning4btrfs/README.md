# Scanning for BTRFS file system

Процесс загрузки Linux (Lite) останавливается, приблизительно на 15с на строке `Scanning for BTRFS file system`.

Возникла после переразметки диска (поменялся UUID для раздела `swap`, раздел `/home` был разбит на 2 и тоже изменился UUID). В [fstab](/e-note/linux/config/fstab) были внесены соотв. правки.

Было такое (вроде логичное) предложение исправить:

> Проблема заключалась в том, что файл **/etc/initramfs-tools/conf.d/resume** содержал старую строку с UUID. После замены на UUID нового свопа проблема исчезла.

но у меня такой файл не нашелся. 

Решение нашел на <https://liberatum.ru/blog/27082>:

```
sudo apt-get purge btrfs-tools  # удаляет оснастку, отвечающую за BTRFS
sudo update-initramfs -ukall    # обновляет индексы временной файловой системы,
                                # используемой ядром при загрузке
sudo apt-get -f install && sudo apt-get autoremove && sudo apt-get autoclean
sudo update-grub
```

После чего следует перезагрузиться.

---

У меня сработало, но из статьи видно, что не у всех. На всякий случай далее:

В итоге, строка `Scanning for BTRFS filesystem` исчезает, но файловая система проверяется те же 15-30 секунд выводится сообщение вида:

    /dev/sda2: clean, 291272/4292608 files, 480345/18174432 blocks

Если данная опция реально замедляет загрузку, то убрать проверку при каждой загрузки можно командой:

    sudo tune2fs -c 10 /dev/sda2  # проверка дисковой партиции будет производится через каждые 10 монтирований.

    sudo tune2fs -c -1 /dev/sda2  # вообще убирает проверку файловой системы.

Конечно, все вышеописанное - очевидный "костыль" и если у кого-то будет более элегантное решение, пишите.

