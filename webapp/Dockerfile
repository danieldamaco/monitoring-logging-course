FROM openjdk:21

WORKDIR /app

# Copiar archivos
COPY petclinic.jar petclinic.jar
COPY jmx_prometheus_javaagent-1.1.0.jar jmx_exporter.jar
COPY config.yml config.yml
COPY petclinic.log /var/log/petclinic.log

# Exponer puertos:
# 8080: app Spring Boot
# 9404: métricas JMX Exporter
EXPOSE 8080 9404

# Comando de arranque con javaagent
ENTRYPOINT ["bash", "-c", "java -javaagent:/app/jmx_exporter.jar=9404:/app/config.yml -jar /app/petclinic.jar > /var/log/petclinic.log 2>&1"]
