# Tensorflow & Monk

This repository contains Monk.io template to deploy Tensorflow either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

## Prerequisites

- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

## Make sure monkd is running

```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository

```bash
git clone https://github.com/monk-io/tensorflow
```

## Load Template

```bash
cd tensorflow
monk load MANIFEST
```

## Let's take a look at the themes I have installed

```bash
foo@bar:~$ monk list tensorflow
✔ Got the list
Type      Template                    Repository  Version  Tags
runnable  tensorflow/tensorflow  local       -        -

```

## Deploy Stack

```bash
foo@bar:~$ monk run tensorflow/tensorflow
? Select tag to run [local/tensorflow/tensorflow] on: mnk
✔ [================================================] 100% tensorflow/tensorflow:latest-jupyter mnk-1
✔ [================================================] 100% alpine:latest mnk-1
✔ Checking/pulling images DONE
✔ Started local/tensorflow/tensorflow

🔩 templates/local/tensorflow/tensorflow
 └─🧊 Peer mnk-1
    ├─🔩 templates/local/tensorflow/tensorflow
    │  └─📦 d26b93f8826f9aafafd07b11b13c0b86-tensorflow-tensorflow-monk-alp
    │     └─🧩 alpine:latest
    └─🔩 templates/local/tensorflow/tensorflow
       └─📦 022273279b4c7ffd2ac42da74dfbbe00-low-tensorflow-tensorflow
          ├─🧩 tensorflow/tensorflow:latest-jupyter
          ├─💾 /var/lib/monkd/volumes/notebooks -> /tf/notebooks
          └─🔌 open 16.171.45.206:8888 (0.0.0.0:8888) -> 8888

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/tensorflow/tensorflow - Inspect logs
        monk shell     local/tensorflow/tensorflow - Connect to the container's shell
        monk do        local/tensorflow/tensorflow/action_name - Run defined action (if exists)
💡 Check monk help for more!
```

## Variables

The variables are in `tensorflow.yml` file. You can quickly setup by editing the values here.

| Variable             | Description  | Default        |
| -------------------- | ------------ | -------------- |
| monk_tensorflow_port | Jupyter Port | 8888           |
| monk_image_tag       | Image tag    | latest-jupyter |

## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```
