# Open API and Knative Camel K examples

Find useful examples about how to expose an Open API specification in a Camel K integration.

## TMF example

Deploy the example running:

```
kamel run --dev --name tmf629 --open-api tmf629.json tmf629DSL.java
```

If you want to disable Knative:

```
kamel run --dev --name tmf629 --open-api tmf629.json tmf629DSL.java --trait knative.enabled=false --trait knative-service.enabled=false --trait jolokia.enabled=true --trait jolokia.discovery-enabled=true -dependency camel:rest --dependency mvn:org.apache.camel.k/camel-k-loader-xml 
```


Then you can test by calling the hello endpoint, ie:

```
$ curl -i https://tmf629-appdev-poc.apps.ocp4.quitala.eu/customer
HTTP/1.1 200 OK
Accept: */*
name: hello
User-Agent: curl/7.68.0
transfer-encoding: chunked

Hello from hello
```

kamel run --dev --name tmf629 --open-api tmf629.json tmf629DSL.java --trait knative.enabled=false --trait knative-service.enabled=false --trait --trait ingress.enabled=true --trait ingress.host=mytmf-appdev-poc.apps.ocp4.quitala.eu


kamel run --dev --name tmf629 --open-api tmf629.json tmf629DSL.java --trait knative.enabled=false --trait knative-service.enabled=false --trait jolokia.enabled=true --trait jolokia.discovery-enabled=true --dependency mvn:org.apache.camel.k/camel-k-loader-xml --property camel.rest.port=8080 --trait container.service-port=8080 --trait ingress.host=mytmf-appdev-poc.apps.ocp4.quitala.eu



