# Add Grafana to Docker Compose File

The open-source platform for monitoring and observability. Grafana allows you to query, visualize, alert on and understand your metrics no matter where they are stored. Grafana helps you to plot the metric that is captured inside Prometheus.

Add Grafana configuration the yaml file

```yaml
version: "3"
services:
  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - 3000:3000
    restart: unless-stopped
    environment:
      - GF_SECURITY_ADMIN_USER=admin
      - GF_SECURITY_ADMIN_PASSWORD=admin
    volumes:
      - ./grafana:/etc/grafana/provisioning/datasources
```

- The service name will be grafana
- Docker image grafana/grafana will be used to create the container
    - As we are not using any tag so the latest image will be pulled
- The Port configuration is 3000:3000
    - This means that the port exposed inside the container and on the host machine is 3000
    - If you want to connect to the Granfana container then you call the host machine on port 3000

### Let’s understand the volume part

- Here we are mounting the ./grafana folder on the Host machine to the /etc/grafana/provisioning/datasources folder inside the docker container.
- This will help to hold the persistent data on the host machine and there will not be any data loss event if the Grafana container is restarted or re-created.
- Environment Variable
    - GF_SECURITY_ADMIN_USER=admin
        - username for the admin user is admin
    - GF_SECURITY_ADMIN_PASSWORD=admin
        - password for the admin user is the password
