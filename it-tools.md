## Summary

* [Website](#website)
* [Run it locally on Docker](#run-it-locally-on-docker)

## Website

https://it-tools.tech/

[Back to top](#summary)

## Run it locally on Docker

### Prerequisites

- [Docker](https://www.docker.com/get-started/)

### Run the container

Run the following command in the terminal:

```bash
docker run -d --name it-tools --restart unless-stopped -p 8080:80 corentinth/it-tools:latest
```

### Stop the container

Run the following command in the terminal:

```bash
docker stop it-tools
```

[Back to top](#summary)