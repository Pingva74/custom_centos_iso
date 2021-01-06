# custom_centos_iso
Создаем свою собственную сборку centos 7 для полностью автоматической установки.

Зачем было сделано:
Для  развертывания нескольких екземпляров centos в virtual box на удаленном сервере в полностью автоматическом режиме.

Создаем точку монтирования, монтируем образ диска

$ mkdir /home/alex/tools/iso
$ mount /home/Download/CentOS-7-x86_64-Minimal-1908.iso /home/alex/tools/iso/

Создаем еще один каталог, копируем в него содержимое /home/alex/tools/iso/

$ mkdir /home/alex/tools/centos
$ cp -rp /home/alex/tools/iso/* /home/alex/tools/centos/

Добавляем наш kickstart в образ
меняем файл isolinux.cfg в папке /home/alex/tools/centos/isolinux на тот что лежит в репе.

Копируем наш kickstart файл в /home/alex/tools/centos/, 


Создаем сам образ:

$ cd /home/alex/tools/centos/
$ mkisofs -o /home/alex/tools/centos-cust.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -V 'CentOS 7 x86_64' -boot-load-size 4 -boot-info-table -R -J -v -T .

Все, инсталим сентось, вопросов задавать и просить что либо ввести ось не будет
user=user
password=fdnjwtynjc
