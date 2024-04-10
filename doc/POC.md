#Локальне встановлення ArgoCD на k3d

Для нашої локальної розробки зробимо кластер
```
k3d cluster create argo
```

використаємо скрипт з офіційного репозиторію ArgoCD
з початку потрібно створити namespace argocd
```
kubectl create namespace argocd
```
перевіримо namespaces
```
kubectl get ns
```

завантажуємо в наш кластер argocd
```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

перевіримо
```
kubectl get pod -n argocd
```


##Готуємо доступ до UI
```
kubectl get svc -n argocd
```

| NAME                                   | TYPE        | CLUSTER-IP     | EXTERNAL-IP  | PORT(S)                     | AGE    |
|----------------------------------------|-------------|----------------|--------------|-----------------------------|--------|
|argocd-applicationset-controller        |   ClusterIP |  10.43.79.237  |  <none>      |  7000/TCP,8080/TCP          |  5m30s |
|argocd-dex-server                       |   ClusterIP |  10.43.142.35  |  <none>      |  5556/TCP,5557/TCP,5558/TCP |  5m30s |
|argocd-metrics                          |   ClusterIP |  10.43.81.111  |  <none>      |  8082/TCP                   |  5m30s |
|argocd-notifications-controller-metrics |   ClusterIP |  10.43.97.243  |  <none>      |  9001/TCP                   |  5m30s |
|argocd-redis                            |  ClusterIP  | 10.43.11.134   |  <none>      |  6379/TCP                   |  5m30s |
|argocd-repo-server                      |  ClusterIP  | 10.43.22.197   |  <none>      |  8081/TCP,8084/TCP          |  5m30s |
|argocd-server                           |  ClusterIP  | 10.43.122.245  |  <none>      |  80/TCP,443/TCP             |  5m29s |
|argocd-server-metrics                   |  ClusterIP  | 10.43.168.23   |  <none>      |  8083/TCP                   |  5m28s |

Активуємо проброс портів
```
kubectl port-forward -n argocd svc/argocd-server 8443:443
```
└─$ Forwarding from 127.0.0.1:8443 -> 8080
Forwarding from [::1]:8443 -> 8080


Тепер можна перейти у браузері за посиланням https://127.0.0.1:8443
Потрібно прийняти ризики недовіренного з'єднання, до того, як не додали сертифікат.

Для першого входу потрібно получити пароль з конфігурації, який був автоматично згенерований
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"| base64 -d;echo
```


Потім можна додавати користувачів, додавати аплікації та робити інші налаштування.


з використанням https://www.youtube.com/watch?v=MeU5_k9ssrs (з 28:00)