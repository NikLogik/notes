---
id: ptk8wj3gwj5ha7wwbuzsuqp
title: Commands
desc: ''
updated: 1684684421223
created: 1684684406802
---

## Полезные команды

### Start/Stop cluster

- Запустить кластер

```sh
minikube start
```

- Проверка статуса

```sh
minikube status
```

- Остановить статус

```sh
minikube stop
```

### Dashboard UI

- Открыть панель управления в браузере

```sh
minikube dashboard
```

### Kuberctl

- Деплой/обновление всех конфигурационных файлов из проекта

```sh
kubectl apply -f [project_foder]/[k8s_folder]
```

- Вывести различие в конф.файлах на кластере

```sh
kubectl diff -f [project_foder]/[k8s_folder]
```

- Удаление задеплоиных файлов

```sh
kubectl delete -f [project_foder]/[k8s_folder]
```
