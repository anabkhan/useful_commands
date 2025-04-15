# Useful commands

## K8S
### Get labels of pod

```sh
kubectl get pods --show-labels
```


### Get logs for all the pods
```sh
gke_prod logs -l app.kubernetes.io/instance=fdp-superbi-brv2 -f -c fdp-superbi-brv2 -n fdp-superbi-brv2-prod
```

### Get pod ip
```sh
kubectl get pod <pod_id> --template '{{.status.podIP}}' -n <ns>
```

### Get events
```sh
gke_prod get events -n fdp-hydra-preprod --sort-by=".metadata.managedFields[0].time"
```

### Search for log4j logs
1. Search for a string in a .gz log
```sh
zgrep "Error message" app.log.2025-04-10.gz
```
3. Search recursively through all .gz files in a directory
```sh
find . -name "*.gz" -exec zgrep "Something went wrong" {} +
```

4. View logs interactively
```sh
zless app.log.2025-04-10.gz
```

4.Decompress and pipe through grep
```sh
zcat app.log.2025-04-10.gz | grep "ERROR"
```

## Gradle/Maven
## Install jar locally (Maven)

```sh
mvn install:install-file -Dfile=/Users/anab.khan/Projects/anab/fdp-plato-meta/meta-visualisation/build/libs/meta-visualisation-1.0-SNAPSHOT.jar -DgroupId=com.flipkart.plato.meta -DartifactId=meta-visualisation -Dversion=1.0 -Dpackaging=jar
```

## JVM Metrics
### VM Args
```
-Dcom.sun.management.jmxremote.port=12345
-Dcom.sun.management.jmxremote.authenticate=false
-Dcom.sun.management.jmxremote.ssl=false
```

### connection
```
service:jmx:rmi:///jndi/rmi://localhost:12345/jmxrmi
```
