These are basic instructions to build a temp cluster for dual stack testing.

It uses Kubernetes in Docker (KinD) to deploy a Kubernetes cluster to your local machine.

You'll need to:

1. Install KinD
2. Deploy a KinD cluster

### Install KinD

Follow the instructions at the [KinD website](https://kind.sigs.k8s.io) for your OS.

The [Quick Start Guide](https://kind.sigs.k8s.io/docs/user/quick-start) has more detailed instructions for installation on different platforms using package managers etc.

You may have to manually add the `kind` program file to your system's PATH variable.

### Deploy a KinD cluster

Once KinD is installed, you can deploy a new KinD cluster. This involves two steps:

1. Create the KinD config file
2. Deploy the KinD cluster

#### Create the KinD config file

Create a new file in your current directory called `kind.yml` with the following config. Feel free to use newer versions of the two images, but you may have to include the digests (different digests exist for different images/architectures). The image repo is [here](https://hub.docker.com/r/kindest/node).

```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: tkb-dual-stack
networking:
  ipFamily: dual
nodes:
- role: control-plane
  image: kindest/node:v1.25.3
- role: worker
  image: kindest/node:v1.25.3
```

#### Deploy the KinD cluster

Run the following command from within the folder containing the `kind.yml` file.

```
$ kind create cluster --config=kind.yml
```

It make take a minute or two for the cluster to create, but your `kubeconfig` file should be updated and you should be ready to test dual stack networking.

#### Stopping and deleting the KinD cluster

You can stop the KinD cluster with the following command.

```
$ kind cluster stop tkb-dual-stack
```

You can delete the KinD cluster with the following command.

```
$ kind cluster delete tkb-dual-stack
```
