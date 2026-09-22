# Workshop: Containerizing and Deplaying a Java Web Application - SpringBoot

## Description
Simple SpringRest App. Invoke it via curl or browser.

Set url parameter **name**

Ex. `http://localhost:9000/greeting?name=Pedro`

### Run app

```shell 
    mvn clean package
    java -jar .\target\virtualization-lab-1.0.0.jar
```

## Evidence PART 1

+ Testing via curl
![evd_curl](/imgs/evd00.png)
+ Testing via browser
![evd_edge](/imgs/evd01.png)

## PART 2
we created and configured the Dockerfile.Then built the image and runned it with:

```shell 
    docker build -t <ExUser>/virtualization-lab:1.0 . 
```

```shell 
    docker run -d `
    --name virtualization-lab-1 `
    -e PORT=9000 `
    -p 34000:9000 `
    ExUser/virtualization-lab:1.0    
```

Then we tested the image in the browser using: http://localhost:34000/greeting?name=Container
![browse_cont](/imgs/evd02.png)

Finally, we runned two isolated instances

```shell 
    docker run -d `
    --name virtualization-lab-2 `
    -e PORT=9000 `
    -p 34000:9000 `
    ExUser/virtualization-lab:1.0    
```

```shell 
    docker run -d `
    --name virtualization-lab-3 `
    -e PORT=9000 `
    -p 34000:9000 `
    ExUser/virtualization-lab:1.0    
```

![3_dif_cont_running](/imgs/evd03.png)

## PART 3

We created `compose.yml` and configured it eith mongodb.

After that, we built and started the compose and tested the url `http://localhost:8087/greeting?name=Compose`

```shell
    docker compose up -d --build
```
![browsing_compose](/imgs/evd04.png)

Finally, we inspected the db from inside its container using:

```shell
    docker compose exec db mongosh
```

and asked for:

```MongoDB
    show dbs
    use workshop
    db.messages.insertOne({ message: "Hello from Docker Compose" })
    db.messages.find()
```

![mongoDB_request](/imgs/evd05.png)