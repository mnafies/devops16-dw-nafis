[node-exporter appserver]
```
docker run -d -p 9100:9100 prom/node-exporter
```
![image](https://user-images.githubusercontent.com/52950376/236685930-a7d37629-f14f-4623-b8dc-ad7b860aed1c.png)
![image](https://user-images.githubusercontent.com/52950376/236685867-b725f85c-291a-4737-bf94-fc98fd80a559.png)

[node-exporter gateway]
```
docker run -d -p 9100:9100 prom/node-exporter
```
![image](https://user-images.githubusercontent.com/52950376/236685942-23072a5e-78fd-48e1-b2ac-e23b8b4377a6.png)
![image](https://user-images.githubusercontent.com/52950376/236685986-f4b9bb4d-6a3a-414f-a4a0-fe1c2166b11c.png)

[prometheus]
prometheus.yml
```
scrape_configs:
- job_name: grafana   
  scrape_interval: 5s
  static_configs:
  - targets:
    - node-exporter-app.nafis.studentdumbways.my.id
    - node-exporter-gate.nafis.studentdumbways.my.id
```

```
docker run -d -p 9090:9090 -v ~/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
```
![image](https://user-images.githubusercontent.com/52950376/236686701-76582220-9915-42e8-838d-deb1e504ee05.png)
![image](https://user-images.githubusercontent.com/52950376/236686586-52d444ba-c2ba-4f1a-8763-8facdbabd230.png)
![image](https://user-images.githubusercontent.com/52950376/236686599-d3f866ad-3c29-4f8e-a420-9a2e026016a7.png)
![image](https://user-images.githubusercontent.com/52950376/236686620-afed4c4e-820f-43c9-8e2b-6d792645a99c.png)


[grafana]
```
docker run -d -p 3000:3000 grafana/grafana
```
![image](https://user-images.githubusercontent.com/52950376/236686745-1c5c0b20-6ebd-4435-8309-96f03d25c888.png)
![image](https://user-images.githubusercontent.com/52950376/236687076-2c338001-3eba-428e-b121-ee0278536ee9.png)

[data source]
![image](https://user-images.githubusercontent.com/52950376/236687188-ada1d6e1-e4b2-4058-9520-0820ca830c3d.png)
![image](https://user-images.githubusercontent.com/52950376/236687255-df4d5ed9-6017-4406-9d94-3dd2e06f2b06.png)
![image](https://user-images.githubusercontent.com/52950376/236687459-40d326d7-7225-48f1-b77d-e854e38f6696.png)
![image](https://user-images.githubusercontent.com/52950376/236687477-ffc81d33-03d3-44ab-8eb6-3a2d19fbe650.png)
![image](https://user-images.githubusercontent.com/52950376/236687535-9f4ca628-60b4-40f6-8a2a-ce472c1d7a12.png)
![image](https://user-images.githubusercontent.com/52950376/236687557-f0f441c8-bae8-491c-a73b-fda8532ec4d9.png)

[dashboard]
![image](https://user-images.githubusercontent.com/52950376/236687671-2f4f9495-17dc-4787-9f06-09789b235226.png)
![image](https://user-images.githubusercontent.com/52950376/236687694-9e204517-b5ae-4bc9-8b51-1de0f61ca587.png)

- CPU
```
100 - (avg by(instance) (irate(node_cpu_seconds_total{mode="idle", job="grafana"}[5m])) * 100)
```
![image](https://user-images.githubusercontent.com/52950376/236689035-d36dab13-27ae-4307-9171-cf11a8dbcf31.png)

- RAM
```
100 * (1 - ((avg_over_time(node_memory_MemFree_bytes[10m]) + avg_over_time(node_memory_Cached_bytes[10m]) + avg_over_time(node_memory_Buffers_bytes[10m])) / avg_over_time(node_memory_MemTotal_bytes[10m])))
```
![image](https://user-images.githubusercontent.com/52950376/236688954-3bcc2e3e-6287-4a47-b731-05aa1fd458f3.png)

- Disk Usage
```
100 - (node_filesystem_avail_bytes / node_filesystem_size_bytes * 100)
```
![image](https://user-images.githubusercontent.com/52950376/236689014-a8af0ef0-4006-4fab-8b82-5deaddf074dd.png)

save dashboard
![image](https://user-images.githubusercontent.com/52950376/236689059-75b4545d-62e9-4f6f-9a62-8a1cef69d736.png)
![image](https://user-images.githubusercontent.com/52950376/236689073-f540ce11-a764-440c-9348-f85b3680f5c0.png)

[alert notification]
![image](https://user-images.githubusercontent.com/52950376/236691207-d1c80f19-7610-4df5-9a57-778fc072cb20.png)


![image](https://user-images.githubusercontent.com/52950376/236689675-fb9e9ef6-13ce-4e27-b052-56cfa60e9864.png)

![image](https://user-images.githubusercontent.com/52950376/236689893-646739c4-6e23-45b7-b62c-9a0e18722519.png)
![image](https://user-images.githubusercontent.com/52950376/236689945-5866019f-d1e2-4519-9aa5-e4d773cab027.png)
![image](https://user-images.githubusercontent.com/52950376/236689962-7cfb8c2e-eda3-4bf9-90b7-866b8c945448.png)
![image](https://user-images.githubusercontent.com/52950376/236689995-f17bbda8-d676-4ed6-bf89-8fc15e5d3868.png)


- CPU Above 20%
![image](https://user-images.githubusercontent.com/52950376/236689644-5a20cabd-c375-4795-9641-3b55279be1d1.png)
![image](https://user-images.githubusercontent.com/52950376/236690391-93f966aa-8826-4d39-8d5e-b48f51875c31.png)

- RAM Above 75%
![image](https://user-images.githubusercontent.com/52950376/236690489-9094bff1-524d-400f-8f54-37cd840488d6.png)
![image](https://user-images.githubusercontent.com/52950376/236690547-e8b8b2fe-8b07-45cc-b7df-d9c4278b365f.png)

![image](https://user-images.githubusercontent.com/52950376/236707346-4eae319f-c762-4639-b534-89e02dfb36a7.png)

