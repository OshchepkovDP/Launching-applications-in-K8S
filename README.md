# Домашнее задание к занятию "`#«Базовые объекты K8S» - Ощепков Дмитрий`"

## Цель задания

В тестовой среде для работы с` Kubernetes`, установленной в предыдущем ДЗ, необходимо развернуть `Pod` с приложением и подключиться к нему со своего локального компьютера.

Чеклист готовности к домашнему заданию
Установленное k8s-решение (например, `MicroK8S`).
Установленный локальный `kubectl`.
Редактор YAML-файлов с подключенным Git-репозиторием.

## Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

Описание `Pod` и примеры манифестов.
Описание `Service`.

## Задание 1. 

Создать `Pod` с именем `hello-world`.
Создать манифест (yaml-конфигурацию) `Pod`.
Использовать `image - gcr.io/kubernetes-e2e-test-images/echoserver:2.2`.
Подключиться локально к `Pod` с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

## Задание 2. Создать Service и подключить его к Pod

Создать `Pod` с именем `netology-web`.
Использовать `image — gcr.io/kubernetes-e2e-test-images/echoserver:2.2`.
Создать `Service` с именем `netology-svc` и подключить к `netology-web`.
Подключиться локально к `Service` с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

Ответ:
Скриншот выполнения команды `kubectl get pods` и локальному подключению к `Pod` с помощью `kubectl port-forward`.
![kubectl_hello.jpg](https://github.com/OshchepkovDP/K8S-Basic-Objects/blob/main/img/kubectl_hello.jpg)
Ссылка на манифест `hello-world-pod.yaml` для создания `Pod` с именем `hello-world` и  развёртывания контейнера `gcr.io/kubernetes-e2e-test-images/echoserver:2.2`
[hello-world-pod.yaml](https://github.com/OshchepkovDP/K8S-Basic-Objects/blob/main/hello-world-pod.yaml)

Скриншот выполнения команды `kubectl get pods` и локальному подключению к `Pod` с помощью `kubectl port-forward`
![kubectl_netology_web.jpg](https://github.com/OshchepkovDP/K8S-Basic-Objects/blob/main/img/kubectl_netology_web.jpg)
Ссылка на манифест `netology-web` для создания`Pod` с именем `netology-web` и развёртывания контейнера `image — gcr.io/kubernetes-e2e-test-images/echoserver:2.2`
[netology-web-pod.yaml](https://github.com/OshchepkovDP/K8S-Basic-Objects/blob/main/netology-web-pod.yaml)
Ссылка на манифест для создания `Service` с именем `netology-svc`
[netology-service.yaml](https://github.com/OshchepkovDP/K8S-Basic-Objects/blob/main/netology-service.yaml)
