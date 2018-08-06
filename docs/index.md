# Getting Started

Welcome to [ELOONG AI](https://eloong.io/) command line docs! Here you'll find information on how to interact with your ELOONG AI instances via the official ELOONG AI command line interface. We do our best to make this documentation clear and user friendly, but if you have unanswered questions, feel free to email us at [steven@eloong.io](mailto:steven@eloong.io).


The ELOONG AI command line interface is on open source on GitHub at [ELOONG-cli](https://github.com/eloongio/eloong-cli). Feel free to submit a pull request or open an issue.


## Installation

The eloong-cli library is installable via the Python package manager `pip`.


#### Install with Python 2
`pip install eloongai -U`


#### Install with Python 3
`pip3 install eloongai -U`


#### Authentication
To authenticate your client, retrieve your secret key from the [verification page](https://eloong.io/edit/verification/) and save your key with the following command:

`eloong ai secret <secret_key>`


## Usage
Here are the supported ELOONG commands which allow you to interact with your GPU instances via the command line. You will need to have entered a valid secret key beforehand.


## Listing your GPU instances
Use the list command to view all of your active GPU instances by ID and hostname.

```bash
vectordash list
```
#### Example
```bash
$ eloongai list
[1] tensorflow-convnet
[2] openai-gym
[3] fastai
```

## Connecting to an instance
Use this command to connect to one of your GPU instances via SSH without having to manually build an SSH command
or manage SSH keys.
Your instance's  `machine_id` can be found by running `eloongai list`.

```bash
eloongai ssh <machine_id>
```

| Name | Description |
| --------------- | ----------- |
| machine_id | ID number of machine to connect to via SSH. |




#### Example
```bash
$ eloongai ssh 1
Connecting via SSH to tensorflow-convnet...
```


## Sending files to an instance

Use this command to transfer files/directories from your local machine to a rented ELOONG AI machine. This builds an `scp` command for you under the hood. The `machine_id` can be found by running `ELOONG AI list`.

```bash
ELOONGAI push <machine_id> <from_path> <to_path>
```

| Name | Description |
| --------------- | ----------- |
| machine_id | ID number of machine to push files to. |
| from_path | Path of local file or directory. |
| to_path | Remove path on ELOONG AI instance. Defaults to the Ubuntu user's home directory. |


#### Example
```bash
$ ELOONGAI push 2 train.py /home/ubuntu/scripts/
Copying data...
```



## Getting files from an instance

Use this command to transfer files/directories from a ELOONG AI instance to your local machine. This builds an `scp` command for you under the hood. The `machine_id` can be found by running `ELOONG AI list`.

```bash
vectordash pull <machine_id> <from_path> <to_path>
```

| Name | Description |
| --------------- | ----------- |
| machine_id | ID number of machine to pull the files from. |
| from_path | Path located on the ELOONG AI instance. |
| to_path | Path of local file or directory. Defaults to the current directory. |




#### Example
```bash
$ ELOONGAI pull 3 /home/ubuntu/model.dat ~/Desktop/
Copying data...
```

## Updating your secret key

Use this command to store your secret token for authentication.
If a previous token had been stored, it will be overwritten with the new token.
You can retrieve your token from the [verification page](https://eloong.io/edit/verification/).

```bash
ELOONGAI secret <secret_key>
```

| Name | Description |
| --------------- | ------- |
| secret_key | Your ELOONG AI account's secret token. |




#### Example
```bash
$ ELOONG AI secret c0nv01utiOnaln3uraln3tw0rk
Secret successfully updated.
```
