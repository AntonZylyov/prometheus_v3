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

������ prometheus �������� ���: [http://localhost:9090/](http://localhost:9090/)

��������� grafana:
```
kubectl port-forward service/prom-grafana 9000:80 -n monitoring
```

������ grafana �������� ���: [http://localhost:9000/](http://localhost:9000/)

�����: admin

������: prom-operator

# ����������

����� ������� ��������, ���������

```
kubectl apply -f benchmark/job/run-benchmark.yaml
```
����  `benchmark/job/run-benchmark.yaml` �������� ��������� � ���, �� �������� ����� ������ ��������.

������ ��� ����������� ����� � apache benchmark (��������� ���: [benchmark/docker](benchmark/docker)) � ������ ��� ������.

## ������� � �������, c ��������� ����������� �� �������

�������:
![By endpoints](grafana-dashboard/by_endpoints.png)
(��� �� �� ���� �������� �� cpu � ������������ ������ ������ � ������� nginx/php/redis)

## ������� � �������, c ��������� ������� � nginx-ingress-controller

��������� nginx-ingress:
```
helm install nginx stable/nginx-ingress -f nginx-ingress/nginx-ingress.yaml
```
������� RPS � � ��������� ��� nginx � ���������������������� �������:
![RPS](grafana-dashboard/rps.png)

������� Latency � ��������� ��� nginx � ���������������������� �������:
![RPS](grafana-dashboard/latency.png)

## �������� �� Error Rate � Latency.

![Alert about RPS](grafana-dashboard/alert_rps.png)

![Alert about latency](grafana-dashboard/alert_latency.png)
 
##  json ��������

json �������� ������� ����� ����� � ����� [grafana-dashboard/dashboard.json](grafana-dashboard/dashboard.json)

