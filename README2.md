## Configs :
    Jaeger :  otel-local-config2.yaml 
    Datadog :  otel-local-config.yaml 

# Commands to follow :

## Docker command to run Jaeger:
    docker run -d --name jaeger \
    -e COLLECTOR_ZIPKIN_HOST_PORT=:9411 \
    -p 5775:5775/udp \
    -p 6831:6831/udp \
    -p 6832:6832/udp \
    -p 5778:5778 \
    -p 16686:16686 \
    -p 14268:14268 \
    -p 14250:14250 \
    -p 9411:9411 \
    jaegertracing/all-in-one:1.27
  
  
## Docker Command to run Collecter with Jaeger Configuration ( otel-local-config2.yaml ) :
      docker run --rm -p 13133:13133 \
      -p 55678-55679:55678-55679 -p 4317:4317 -p 8888:8888 -p 55680:55680 \
      -v "${PWD}/otel-local-config2.yaml":/otel-local-config.yaml \
      --name otelcol otel/opentelemetry-collector \
      --config otel-local-config.yaml; \

## Docker Command to run Collecter with Datadog Configuration ( otel-local-config.yaml ) :
      docker run --rm -p 13133:13133 \                                    
      -p 55678-55679:55678-55679 -p 4317:4317 -p 8888:8888 -p 55680:55680 \
      -v "${PWD}/otel-local-config.yaml":/otel-local-config.yaml \ 
      --name otelcol otel/opentelemetry-collector-contrib \
      --config otel-local-config.yaml; \
      
## Run Go Project :
      go mod tidy
      go run .
