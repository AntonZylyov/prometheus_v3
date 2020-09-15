# ��������� � �������������

���� ���������� myapp ���, ������� ���:

```
kubectl create namespace myapp
```

���������� ���������� �� helm:

```
helm install mysuperapp ./helm -n myapp
```

���� ���������� monitoring ���, ������� ���:
```
kubectl create namespace monitoring
```

���������� prometheus � grafana:
```
helm install prom stable/prometheus-operator -f prometheus/prometheus.yaml -n monitoring --atomic
```

��������� prometheus:
```
kubectl port-forward service/prom-prometheus-operator-prometheus 9090  -n monitoring
```

������ prometheus �������� ���: http://localhost:9090/


# ����������
