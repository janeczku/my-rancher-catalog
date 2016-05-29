# DataDog Agent

This template deploys a [DataDog](https://www.datadoghq.com/) agent stack consisting of the official [docker-dd-agent](https://www.github.com/Datadog/docker-dd-agent) image and a configuration sidekick that enhances integration with Rancher:

* Report the names of hosts to DataDog
* Export host labels as DataDog host tags
* Export service labels as DataDog metric tags

## Service Discovery
Please refer to the Datadog documentation [here](http://docs.datadoghq.com/guides/servicediscovery/) to learn how to provide configuration templates for Service Discovery in etcd or Consul.