# Prometheus and Grafana installation using Docker compose

- Create a Docker Compose file
- Add Prometheus Service to Docker Compose File
  - Add Prometheus Configuration File
- Add Grafana to Docker Compose File
- Final Docker Compose File
- Start the Services
- Check Prometheus service is running
- Check Grafana is Running
- References

we will learn to install `Prometheus` and `Grafana` using Docker Compose. Installation using Docker Compose will be Operating system agnostic. Prometheus and Grafana are monitoring tools for your application.

Using Prometheus you can collect metrics from different sources like NodeJs, Python, etc application, and then use `Grafana` to plot meaningful graphs using the collected data.

## Create a Docker Compose file

You will need a docker-compose file to write the configuration for your services and then deploy the services using the docker-compose file.

Let’s create a new file `prometheus-grafana.yml`

> touch prometheus-grafana.yml

## Add Prometheus Service to Docker Compose File

```yaml
version: "3"
services:
  prometheus:
    image: prom/prometheus
    volumes:
      - "./prometheus.yml:/etc/prometheus/prometheus.yml"
    ports:
      - 9090:9090
```

- The service name will be prometheus
- `prom/prometheus` is the docker image being used for container creation
  - As we are not using any tag so latest image will be pulled up.
- The Port configuration is 9090:9090
  - This means that the port exposed inside the container and on the host machine is 9090
  - If you want to connect to this container then you call the host machine on port 9090

### Let’s understand the volume part

- Here we are mounting the prometheus.yml file on the Host machine to the /etc/prometheus/prometheus.yml file inside the docker container.
- This will help to write the new configuration which the Prometheus container can understand.

## Add Prometheus Configuration File

Prometheus needs to know the configuration for scraping. Create `prometheus.yml` file in the same folder where you have created the `prometheus-grafana.yml` and then you can add the scraping configuration later on.

```bash
touch prometheus.yml
```
