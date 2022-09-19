# Weather app with Helm
This example should be used in a kubernetes environment.

## purpose
with the help of this code, we can install weather app in kubernetes environment and scale it as per our needs, This is also integrated with New Relic APM agent. Please define your licence key in value.yaml and it will start reporting to new relic.

For Free New Relic account --> https://one.newrelic.com

## usage
Get helm version 3.x https://helm.sh/

Get kubectl https://kubernetes.io/docs/tasks/tools/

create a helm config values.yaml and provide necessary details
```
# This file defines the values for weather app deployment
weather_app:
  nrappname: weather-app-helm
  name: weather-app
  cpuMin: 100m
  cpuMax: 300m
  memoryMin: 100Mi
  memoryMax: 300Mi
  imageVersion: bhattd5/weather-app-newrelic:v1
  nrLicKey: <<licKey>>

servicePort:
  port: 3000

```
Deploy script to your namespace:
```
helm upgrade --install -n "namespace" -f values.yaml weather-app .
```
uninstall with
```
helm uninstall -n "namespace" weather-app
```
verify installation
```
kubectl get pods -n "namespace"
kubectl get svc -n "namespace"
```
output:

![image](https://user-images.githubusercontent.com/29163790/190945866-a87fec41-c57a-4914-b454-3725d7cd3145.png)

![image](https://user-images.githubusercontent.com/29163790/190945923-56191ae4-20ca-41c8-9f04-9d72cd8b4d09.png)


## New Relic Metrics

Application Summary

![image](https://user-images.githubusercontent.com/29163790/190945172-e11a41f3-963f-4972-9dab-bf20b255616a.png)
![image](https://user-images.githubusercontent.com/29163790/190945400-e9843981-6b88-4e23-a423-1e32a0fe0fec.png)


SVC Map
![image](https://user-images.githubusercontent.com/29163790/190945310-95ea675d-55a3-4688-90dc-6d31145766e0.png)

Transaction Overview
![image](https://user-images.githubusercontent.com/29163790/190945428-afa4abc8-0e92-4c93-b1fa-ea381c782ec5.png)
![image](https://user-images.githubusercontent.com/29163790/190945511-e41dad3a-d1db-463c-98eb-c0c7c94df9eb.png)
![image](https://user-images.githubusercontent.com/29163790/190945546-35d20a39-cbd7-4d79-a9e3-3253f2935dfd.png)
![image](https://user-images.githubusercontent.com/29163790/190945480-451593b1-1d7b-45dd-a0ab-b71873f733be.png)





