## Download  attached fluentd-cm.yaml and fluentd-ds.yaml
```
kubectl apply -f fluentd-cm.yaml   # please review the changes to make sure all the metrics and configurations in there
kubectl apply -f fluentd-ds.yaml   # please update with your image name
```cli
## Troubleshooting steps

1.	Exec into fluentd deamonset pod and run the curl command http://<fluentd-pod-ip>:24231/metrics and you should see the prometheus metrics 
root@fluentd-g9m57:/home/fluent# curl http://10.240.0.20:24231/metrics  # Please use your fluentd pod IP address 

TYPE fluentd_input_log_count counter
HELP fluentd_input_log_count The total number of incoming records
fluentd_input_log_count{tag="fml.model_logs",hostname="fluentd-g9m57",worker="0"} 1958.0
…

2.	If above step successful, under 5 minutes, you should see  prometheus metrics under InsightsMetricsTable



 

