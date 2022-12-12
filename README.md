# HPC Cluster

This is the starting point for deploying an HPC Cluster with
[juju](https://juju.is).

## Prerequisites

Install snap:

```
apt install snapd
```

Install juju:

```
snap install juju --channel=3.0/stable
```

Set up juju (for lxd, "localhost-localhost"):

```
juju bootstrap
juju add-model default
```

## To Monitor

Set up monitor (in separate terminal window):

```
juju status --watch 5s --relations
```

## Basic Cluster

Note: Initial version of
[hpc-cluster-basic.yaml](./hpc-cluster-base.yaml)
is set up to pull local charms from the current directory. This will
be updated once the charms are in the charmhub store.

### Deploy

Deploy the cluster:

```
juju deploy hpc-cluster
```

### Scaling

Increase head (from 1 to 2):

```
juju add-unit -n 1
```

Increase interactive (from 1 to 4):

```
juju add-unit interactive -n 3
```

Increase compute (from 1 to 10):

```
juju add-unit compute -n 9
```
