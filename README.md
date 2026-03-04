Домашнее задание к занятию «Очереди RabbitMQ» Николай Чернов

Задание 1. Установка RabbitMQ
Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ. Добавьте management plug-in и зайдите в веб-интерфейс.

Итогом выполнения домашнего задания будет приложенный скриншот веб-интерфейса RabbitMQ.

<img width="1365" height="664" alt="image" src="https://github.com/user-attachments/assets/4b03aae9-2be7-491c-b83a-48f041e77adc" />

Задание 2. Отправка и получение сообщений
Используя приложенные скрипты, проведите тестовую отправку и получение сообщения. Для отправки сообщений необходимо запустить скрипт producer.py.

Для работы скриптов вам необходимо установить Python версии 3 и библиотеку Pika. Также в скриптах нужно указать IP-адрес машины, на которой запущен RabbitMQ, заменив localhost на нужный IP.

$ pip install pika
Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот. После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта

В качестве решения домашнего задания приложите оба скриншота, сделанных на этапе выполнения.

<img width="1366" height="665" alt="image" src="https://github.com/user-attachments/assets/afd30083-a5c5-473e-bef4-7cb28feda116" />

<img width="406" height="126" alt="image" src="https://github.com/user-attachments/assets/3ecceddc-e70e-44bf-bef1-e6c631eb6921" />

Задание 3. Подготовка HA кластера
Используя Vagrant или VirtualBox, создайте вторую виртуальную машину и установите RabbitMQ. Добавьте в файл hosts название и IP-адрес каждой машины, чтобы машины могли видеть друг друга по имени.

Пример содержимого hosts файла:

$ cat /etc/hosts
192.168.0.10 rmq01
192.168.0.11 rmq02

После этого ваши машины могут пинговаться по имени.

Затем объедините две машины в кластер и создайте политику ha-all на все очереди.

В качестве решения домашнего задания приложите скриншоты из веб-интерфейса с информацией о доступных нодах в кластере и включённой политикой.

<img width="1364" height="665" alt="image" src="https://github.com/user-attachments/assets/939c52a9-108d-482c-81fb-61f21b92104c" />

<img width="1366" height="664" alt="image" src="https://github.com/user-attachments/assets/c4a79a47-e23f-4b92-8a96-9dd48a4cb2dc" />


Также приложите вывод команды с двух нод:

$ rabbitmqctl cluster_status

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0297b9b5-7c83-499b-8b52-f98afe6db47b" />
<img width="962" height="639" alt="image" src="https://github.com/user-attachments/assets/89f5b55e-6d66-44df-bfff-220a5d397eec" />


Для закрепления материала снова запустите скрипт producer.py и приложите скриншот выполнения команды на каждой из нод:


$ rabbitmqadmin get queue='hello'
<img width="591" height="199" alt="image" src="https://github.com/user-attachments/assets/81123e1a-799c-4fa2-97bc-3d899d79d099" />


После чего попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.

Приложите скриншот результата работы второго скрипта.
