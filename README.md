# Workshop: Containerizing and Deplaying a Java Web Application

## Description
Simple SpringRest App. Invoke it via curl or browser.

Set url parameter **name**

Ex. `http://localhost:9000/greeting?name=Pedro`

### Run app

```shell 
    mvn clean package
    java -jar .\target\virtualization-lab-1.0.0.jar
```

## Evidence

+ Testing via curl
![evd_curl](/imgs/evd00.png)
+ Testing via browser
![evd_edge](/imgs/evd01.png)