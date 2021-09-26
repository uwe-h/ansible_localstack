# Example for testing System Manager Ansible with Localstack

## Introduction

In this quite simple approach, we use endpoint url mechanism for directly forwarding from our EC2 Simulation (Docker Container) to the mock implementation (i.e., localstack).

![Architecture](architecture.png "Architecture")

## About Me

I am a full-blooded software engineer focused on AWS, Cloud, and building high-quality software. I like to learn programming languages and my belief is that multi-lingual language skills can help you to become a better programmer through learning from diverse language concepts. Further, I have interest in developing highly effective and efficient teams.

## Disclaimer

This example is just an illustration how you can combine ec2 simulation with localstack for testing ansible. It is not a blueprint for doing productive code or proper unit testing.


## Demo
1. `docker-compose run ec2sim`
1. `./run_tests.sh`

## Variants

* [HTTP Proxy with Local Stack](https://github.com/uwe-h/ansible_localstack_proxy)

* [HTTP Proxy with Playpack Requests](https://github.com/uwe-h/ansible_proxy_playback)


## Implementation

### EC2 Simulation (EC2 Sim)

1. Set S3_URL to localstack(`docker-compose.yml`)
2. Add an endpoint_url with empty string to ansible (`ansible.yml`).
3. Add endpoint_url to all aws cli commands (`ansible.yml`)
4. Add endpoint_url to extra_vars in test_ansible.py and set it to the local stack instance (`test_ansible.py`)
5. put to all boto3 clients the endpoint_url parameter (`test_ansible.py`)

## Limitation
* Not all ansible modules allows to provide and endpoint url as the S3 example above

