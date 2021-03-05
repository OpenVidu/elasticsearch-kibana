# Elasticsearch and Kibana

This is an easy to deploy Elasticsearch and Kibana ready to work for OpenVidu Pro.

# Prerequesites

- Docker
- Docker compose
- Git

# Installation

1. Git clone this repository in any directory:

```
git clone https://github.com/OpenVidu/elasticsearch-kibana.git
```

2. Fill the parameters of the .env file. This parameters are mandatory:

- `DOMAIN_OR_PUBLIC_IP`: Domain or public IP where your installing Elasticsearch and Kibana.
- `CERTIFICATE_TYPE`: The type of certificate you want to use:
    - `selfsigned`: Self signed certificate. Not recommended for production use. Users will see an ERROR when connected to web page.
    - `letsencrypt`: Generate a new certificate using letsencrypt. Please set the required contact email for Let's Encrypt in `LETSENCRYPT_EMAIL` variable. 
    You need also a FQDN (Fully Qualified Domain Name) for letsencrypt to work properly.
    - `owncert`: Valid certificate purchased in a Internet services company. Please put the certificates files inside folder `./owncert` with names `certificate.key` and `certificate.cert`.
- `LETSENCRYPT_EMAIL`: Fill this if you're using `CERTIFICATE_TYPE=letsencrypt`.
- `ELASTICSEARCH_USERNAME`: Username for Elasticsearch
- `ELASTICSEARCH_PASSWORD`: Password for the Elasticsearch user.

3. Execute the deployment with:

```
docker-compose up -d
```

And that's it. You will have your Elasticsearch and Kibana ready at:

- Elasticsearch: `https://<DOMAIN_OR_PUBLIC_IP>/`
- Kibana: `https://<DOMAIN_OR_PUBLIC_IP>/kibana`

# Configure it for OpenVidu

You just need to add/modify this properties in your OpenVidu installation at `/opt/openvidu/.env`:

```
OPENVIDU_PRO_ELASTICSEARCH_HOST=https://<DOMAIN_OR_PUBLIC_IP>:443/
OPENVIDU_PRO_KIBANA_HOST=https://<DOMAIN_OR_PUBLIC_IP>:443/kibana/
ELASTICSEARCH_USERNAME=<ELASTICSEARCH_USERNAME>
ELASTICSEARCH_PASSWORD=<ELASTICSEARCH_PASSWORD>
```
