# Sykube

[![CircleCI](https://circleci.com/gh/sylabs/sykube/tree/master.svg?style=svg)](https://circleci.com/gh/sylabs/sykube/tree/master)

Sykube is inspired by [Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/) and allows
to quickly deploy a localized multi-node K8S cluster (2 nodes by default) on a single machine. The K8S cluster
is setup with the help of [Singularity-CRI](https://github.com/sylabs/singularity-cri) and
[Singularity OCI](https://sylabs.io/guides/3.2/user-guide/oci_runtime.html).

It's easy to use and automatically install a Kubernetes dashboard.

## Quick start

Sykube requires Singularity (a version >= [3.2](https://github.com/sylabs/singularity/tree/v3.2.0) is recommended).

### Sykube installation

To install sykube on your machine, just run:

```bash
sudo singularity run library://sykube
```

The above command does two things, it downloads and cache the image used by Sykube and install sykube binary
in ``/usr/local/bin`` path

### Setup a K8S cluster

* To start a K8S cluster installation, just type:

```bash
sykube init
```

May take few minutes depending of your internet bandwidth.

* If you are familiar with K8S, you can generate a ``kubectl`` alias with:

```bash
sykube kubectl
```

To inject a ``kubectl`` alias into your current shell session.

* You can also access to K8S dashboard with:

```bash
sykube dashboard
```

If you have ``xdg-open`` installed, it will automatically open your default internet browser, and if ``xclip`` is
also installed the token will be automatically set in your clipboard, then you would just have to paste in the
corresponding token page field.

## From source

To build it from this repository:

```bash
git clone https://github.com/sylabs/sykube
cd sykube
sudo singularity build /tmp/sykube.sif sykube.def
sudo singularity run /tmp/sykube.sif
sykube init --local-image /tmp/sykube.sif
```
