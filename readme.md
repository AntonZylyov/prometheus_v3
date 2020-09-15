# Установка и инициализация

Если неймспейса myapp нет, создать его:

```
kubectl create namespace myapp
```

Установить приложение из helm:

```
helm install mysuperapp ./helm -n myapp
```

Если неймспейса monitoring нет, создать его:
```
kubectl create namespace monitoring
```

Установить prometheus и grafana:
```
helm install prom stable/prometheus-operator -f prometheus/prometheus.yaml -n monitoring --atomic
```

Запустить prometheus:
```
kubectl port-forward service/prom-prometheus-operator-prometheus 9090  -n monitoring
```

Теперь prometheus доступен тут: http://localhost:9090/


# Результаты
