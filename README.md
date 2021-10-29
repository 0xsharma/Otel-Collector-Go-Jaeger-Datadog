## Configs :
    Jaeger :  otel-local-config2.yaml 
    Datadog :  otel-local-config.yaml 

# Commands to follow :

## Docker command to run Jaeger:
    docker run --net=host  jaegertracing/all-in-one:1.27
  
## Docker Command to run Collecter with Jaeger Configuration ( otel-local-config2.yaml ) :
      docker run --net=host -v "${PWD}/otel-local-config2.yaml":/otel-local-config.yaml otel/opentelemetry-collector --config otel-local-config.yaml;

## Docker Command to run Collecter with Datadog Configuration ( otel-local-config.yaml ) :
      docker run --net=host -v "${PWD}/otel-local-config.yaml":/otel-local-config.yaml otel/opentelemetry-collector-contrib --config otel-local-config.yaml

## Docker Command to run Collecter with both Configurations :
      docker run --net=host -v "${PWD}/otel-local-config3.yaml":/otel-local-config.yaml otel/opentelemetry-collector-contrib --config otel-local-config.yaml
      
## Run Go Project :
      go mod tidy
      go run .
