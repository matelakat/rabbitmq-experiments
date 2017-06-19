# RabbitMQ Experiments

The goal is to find out how to configure an HA RabbitMQ cluster on SLES12SP1

## Infrastructure/Requirements

These are the settings baked into the code. If you want to change any of the
settings, you need to change the file `vars.yml`

 * Have a bridge on your host, called `susebr`
 * Have that bridge live on a network with `192.168.40.x`
 * The machines will use addresses `192.168.40.[151,152,153]`
 * Clouddata base is `http://192.168.0.200`

## Usage

To start the machines, simply type:

    vagrant up

After you change something on the ansible side, you want to re-run it with:

    vagrant provision
