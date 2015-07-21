This Vagrantfile creates a multi-machine environment provisioned by Salt that consists of the following:

* `elasticsearch`:
    - This is an Ubuntu 14.04 box with Elasticsearch 1.6.
* `elastalert`:
    - This is an Ubuntu 14.04 box with:
        - [ElastAlert](https://github.com/Yelp/elastalert) and dependencies
        - Python 2.6 and 2.7
        - Supervisor

Upon instantiation, the `elastalert` box will be provisioned to use `elasticsearch` as its Elasticsearch host. Moreover, ElastAlert will be automatically started under `supervisord` using the configuration in `salt/roots/salt/elastalert/config.yaml` with the rules (if any) specified in `salt/roots/salt/elastalert/rules`. Combined with the scripted loading of data for the `elasticsearch` box, this can be a convenient way to test rules in an automated fashion without a persistent Elasticsearch environment.

The automatic configuration of `/etc/hosts` relies on the Vagrant plugin `vagrant-hostmanager`, and so this plugin is required in order to use this Vagrantfile.
