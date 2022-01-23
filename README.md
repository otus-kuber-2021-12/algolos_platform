# algolos_platform
algolos Platform repository

HomeTask2:

Задание:
Разберитесь почему все pod в namespace kube-system восстановились после удаления.

Поды etcd, kube-apiserver,  kube-controller-manager,  kube-scheduler являются статическими и управляются kubelet-ом(монифесты со статическими подами лежат в /etc/kubernetes/manifests папке), он следит за их состоянием и перезапускает в случае падения.
Поды core-dns и kube-proxy управляются механизмами Kubernetes (Deployment и DaemonSet) и восстанавливаются в силу того, что kube-controller-manager следит за состоянием кластера и при любых «непредвиденных» изменениях стремится привести его к состоянию, описанному в etcd.


Проделана следующая работа.
1. Установлен minikube;
2. Создан и протестрован докер файл на основе python:3.9.0-alpine образа;
3. Загружен докер образ с web-server на docker-hub;
4. Создан и протестрован манифест пода для запуска web-server в minikube;
5. Дополнен монифест web-server описанием инит пода и volume.
6. Протестирован запуск web-server с инит подом.

Дополнительно:

Сформировал манифест и запустил frontend pod с добавленными перменными окружения, которые были взяты из оригинального описания.