**Переменные для всех репозиториев (на группу):**

`$CI_REGISTRY` - адрес docker - registry.rebrainme.com

`$CI_REGISTRY_PASSWORD`

`$CI_REGISTRY_USER`

2 файловые переменные, для авторизации в GKE

`$config` - kubeconfig

`$serviceaccountkey` - key для GKE

Если просто K8s кластер, достаточно задать $config = содержимое вашего kubeconfig (учетка с правами деплоя)

**FRONT:**

`$VUE_APP_BACKEND_URL`  - адрес backend в формате http://server. Прописывается в js файлах в процессе сборки.

**BACKEND:**

`$CI_MASTER_APP_KEY`  - ключ на основе которого Laravel будет шифровать данные `base64:be67YT816I68/NptQzuBP+iXU3oAYxndrGPLeKKNszs=`

`$CI_MASTER_DB_HOST` - адрес базы

`$CI_MASTER_DB_PORT` - порт

`CI_MASTER_DB_USER` - пользователь и имя базы (делаем одинаковым, чтобы экономить на создании переменных)

`$CI_MASTER_DB_PASSWORD` - пароль

**Образы**

Для сборки "толстого" образа берем Dockerfile (может не собраться на rpm-based т.к. там podman)

Исходники честно украдены у https://github.com/laradock  в контейнер добавлен Nginx и supervisord 


**Полезные ссылки**

* https://devops.stackexchange.com/questions/4013/how-to-pull-a-docker-image-from-a-private-docker-registry-using-helm
* https://github.com/laradock
* https://jfrog.com/blog/helm-charts-best-practices/
* https://www.alibabacloud.com/blog/helm-charts-and-template-basics---part-2_595490
* https://hackernoon.com/the-art-of-the-helm-chart-patterns-from-the-official-kubernetes-charts-8a7cafa86d12
* https://docs.bitnami.com/tutorials/create-your-first-helm-chart/
* https://medium.com/gammastack/mounting-environment-variables-safely-with-kubernetes-secrets-and-helm-chart-764420dc787b
* https://habr.com/ru/company/flant/blog/423239/
