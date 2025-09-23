# Домашнее задание к занятию «Запуск приложений в K8S»

## Задание 1. Создать Deployment и обеспечить доступ к репликам приложения из другого Pod
1. Создать Deployment приложения, состоящего из двух контейнеров — nginx и multitool. Решить возникшую ошибку.

Создан Deployment. 

<img width="631" height="148" alt="image" src="https://github.com/user-attachments/assets/329a5129-0240-42be-977e-d555aaa4b45f" />

[Ссылка на манифест deployment](https://github.com/vladmgb/kuber-1.3/blob/main/deployment.yaml)

Ошибка была связана с тем, что nginx и multitool по-умолчанию используют порт 80. multitool перенастроил на порт 8080.
   
2. После запуска увеличить количество реплик работающего приложения до 2.

Установил ``replicas: 2``
   
3. Продемонстрировать количество подов до и после масштабирования.

<img width="568" height="101" alt="image" src="https://github.com/user-attachments/assets/021d5a00-3912-4d8e-99f6-3beea99ccb95" />
   
4. Создать Service, который обеспечит доступ до реплик приложений из п.1.

   Создан Service.

<img width="650" height="78" alt="image" src="https://github.com/user-attachments/assets/99514746-4800-4a46-9d0b-2f505efb2c05" />

   [Ссылка на манифест service](https://github.com/vladmgb/kuber-1.3/blob/main/service2.yaml)

Проверка доступности портов.

   <img width="1150" height="388" alt="image" src="https://github.com/user-attachments/assets/0b3f059d-dc4e-462f-8542-ec52949eda3a" />


6. Создать отдельный Pod с приложением multitool и убедиться с помощью curl, что из пода есть доступ до приложений из п.1.

Создан отдельный Pod multitool.

   <img width="588" height="125" alt="image" src="https://github.com/user-attachments/assets/243e1ce9-503c-4f8e-af60-451f24684215" />

Проверка доступа до приложений из п.1 проходит.

<img width="1149" height="416" alt="image" src="https://github.com/user-attachments/assets/b74eda4f-5878-417e-8559-9efff25d5895" />


## Задание 2. Создать Deployment и обеспечить старт основного контейнера при выполнении условий
1. Создать Deployment приложения nginx и обеспечить старт контейнера только после того, как будет запущен сервис этого приложения.
2. Убедиться, что nginx не стартует. В качестве Init-контейнера взять busybox.
3. Создать и запустить Service. Убедиться, что Init запустился.
4. Продемонстрировать состояние пода до и после запуска сервиса.

