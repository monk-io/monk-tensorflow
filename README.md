# Tensorflow & Monk
This repository contains Monk.io template to deploy Tensorflow either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/Burakhan/monk-tensorflow
```

## Load Template
```bash
cd monk-tensorflow
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-tensorflow
✔ Got the list
Type      Template                    Repository  Version  Tags
runnable  monk-tensorflow/tensorflow  local       -        -

```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-tensorflow/tensorflow
? Select tag to run [local/monk-postgresql-cluster/stack] on: postgres
✔ Starting the job: local/monk-postgresql-cluster/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
Started local/monk-tensorflow/tensorflow

🔩 templates/local/monk-tensorflow/tensorflow
 └─🧊 Peer mnk-1
    ├─🔩 templates/local/monk-tensorflow/tensorflow
    │  └─📦 d26b93f8826f9aafafd07b11b13c0b86-tensorflow-tensorflow-monk-alp
    │     └─🧩 alpine:latest
    └─🔩 templates/local/monk-tensorflow/tensorflow
       └─📦 022273279b4c7ffd2ac42da74dfbbe00-low-tensorflow-monk-tensorflow
          ├─🧩 tensorflow/tensorflow:latest-jupyter
          ├─💾 /var/lib/monkd/volumes/notebooks -> /tf/notebooks
          └─🔌 open 16.171.45.206:8888 (0.0.0.0:8888) -> 8888

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/monk-tensorflow/tensorflow - Inspect logs
        monk shell     local/monk-tensorflow/tensorflow - Connect to the container's shell
        monk do        local/monk-tensorflow/tensorflow/action_name - Run defined action (if exists)
💡 Check monk help for more!
```


## Variables
The variables are in `tensorflow.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| monk_tensorflow_port          | Jupyter Port, Default: 8888 	               |
| monk_image_tag             	| Image tag, Default latest-jupyter                      	|
| volume_data             	    | Notebooks path                      	|


## 
You can view the token information you need to log in with the `monk logs` command.

## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```