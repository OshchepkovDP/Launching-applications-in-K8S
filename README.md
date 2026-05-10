# Домашнее задание к занятию "`#«Запуск приложений в K8S» - Ощепков Дмитрий`"

## Цель задания

В тестовой среде для работы с `Kubernetes`, установленной в предыдущем ДЗ, необходимо развернуть `Deployment` с приложением, состоящим из нескольких контейнеров, и масштабировать его

## Чеклист готовности к домашнему заданию

Установленное k8s-решение (например, `MicroK8S`).
Установленный локальный `kubectl`.
Редактор YAML-файлов с подключенным Git-репозиторием.

## Задание 1. Создать Deployment и обеспечить доступ к репликам приложения из другого Pod

Создать `Deployment` приложения, состоящего из двух контейнеров — `nginx` и `multitool`. Решить возникшую ошибку.
После запуска увеличить количество реплик работающего приложения до 2.
Продемонстрировать количество подов до и после масштабирования.
Создать `Service`, который обеспечит доступ до реплик приложений из п.1.
Создать отдельный `Pod` с приложением `multitool` и убедиться с помощью `curl`, что из пода есть доступ до приложений из п.1.

## Задание 2. Создать Deployment и обеспечить старт основного контейнера при выполнении условий

Создать `Deployment` приложения `nginx` и обеспечить старт контейнера только после того, как будет запущен сервис этого приложения.
Убедиться, что `nginx` не стартует. В качестве Init-контейнера взять `busybox`.
Создать и запустить `Service`. Убедиться, что `Init` запустился.
Продемонстрировать состояние пода до и после запуска сервиса.

Ответ:
**Задание 1**

Скриншот выполнения команды `kubectl get pods` подтверждающией наличие одного `Deployment` приложения, состоящего из двух контейнеров — `nginx` и `multitool`.
![multitool-nginx-1pods.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/multitool-nginx-1pods.jpg)

Скриншот выполнения команды `kubectl scale deployment multitool-nginx-deployment --replicas=2` подтверждающий масштабирование `Deployment` приложения до 2-х.
![multitool-nginx-2pods.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/multitool-nginx-2pods.jpg)

Скриншот подтверждения доступа до реплик приложений из п.1 в том числе и для отдельного `Pod` с приложением `multitool`.
![multitool-service.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/multitool-service.jpg)

Ссылка на манифест `deployment-multitool.yaml` для создания `Deployment` приложения, состоящего из двух контейнеров — `nginx` и `multitool`
[deployment-multitool.yaml](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/deployment-multitool.yaml)

Ссылка на манифест `nginx-service.yaml` для обеспечения доступа к репликам
[nginx-service.yaml](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/nginx-service.yaml)

**Задание2**

Скриншот выполнения команды `kubectl get pods` подтверждающей, что `nginx` не стартует.
![nginx_init_error.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/nginx_init_error.jpg)

Скриншот выполнения команды `kubectl describe pod -l app=nginx-init` подтверждающей, что `nginx-init` запустился и ждёт ответа. Сервис ещё не запущен.
![Adding_nginx-service.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/Adding_nginx-service.jpg)

Скриншот состояния пода после запуска сервиса
![Curl_nginx_init_service.jpg](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/img/Curl_nginx_init_service.jpg)

Ссылка на манифест `nginx-init-deployment.yaml` создающий `Deployment` приложение `nginx` с использованием образа `busybox`
[nginx-init-deployment.yaml](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/nginx-init-deployment.yaml)

Ссылка на манифест `nginx-init-service.yaml` создающий сервис для обеспечения доступа к поду
[nginx-init-service.yaml](https://github.com/OshchepkovDP/Launching-applications-in-K8S/blob/main/nginx-init-service.yaml)
