# sprinBoot-s2i
### this small guide is used to create a spring-boot example project using s2i
requirements:
Openshift 4 cluster
openshift cli 
<br />
<br />

##Step 1: Create a new project namespace on your cluseter
```
oc new-project spring-boot-s2i
```

##Step 2: Create a new application inside our project
```
oc new-app registry.access.redhat.com/redhat-openjdk-18/openjdk18-openshift~https://github.com/snowdrop/rest-http-example ref=2.3.4-2-rehat --name spring-boot-s2i
```

##Step 3: Verify that out application is running
```
oc get pods



example output:
NAME                      READY   STATUS    RESTARTS   AGE
spring-boot-s2i-1-build   1/1     Running   0          43s
```

##Step 4: Get the service name
```
oc get svc


example output:
NAME              TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
spring-boot-s2i   ClusterIP   xxx.xx.xxx.xxx   <none>        xxxxxxx                      84s
```

##Step 5: We will expose the service so it can be accessed from a browser
```
oc expose svc/spring-boot-s2i
```

##Step 6: Get the route
```
oc get route 

example outpuut:
NAME              HOST/PORT                                                  PATH   SERVICES          PORT       TERMINATION   WILDCARD
spring-boot-s2i   <route displayed here>         spring-boot-s2i   8080-tcp   


All we have to do now is paste the route in a browser and see our results
```
