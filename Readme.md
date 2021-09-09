# Example for testing SSM Ansible with Localstack and an HTTPS Proxy

## Introduction

## Disclaimer

This example is just a example how you can combine a http proxy with local stack for testing ansible. It is definitely a blueprint for doing secure releases or proper unit testing.

## Implementation

### EC2 Simulation (EC2 Sim)

1. Set S3_URL to localstack(`docker-compose.yml`)
2. Add an endpoint_url with empty string to ansible (`ansible.yml`).
3. Add endpoint_url to all aws cli commands (`ansible.yml`)
4. Add enpoint_url to extra_vars in test_ansible.py and set it to the local stack instance (`test_ansible.py`)
5. put to all boto3 clients the endpoint_url parameter (`test_ansible.py`)

## Limitation
* Not all ansible modules allows to provide and endpoint url as the S3 example above

