# MLflow-Demo

### dagshub
[dagshub](https://dagshub.com/)

MLFLOW_TRACKING_URI=https://dagshub.com/buzaXnov/MLflow-Demo.mlflow \
MLFLOW_TRACKING_USERNAME=buzaXnov \
MLFLOW_TRACKING_PASSWORD=c2f97b6e1897763abc2b78d3781adbbf30ba2026 \
python example.py

Run this to export as env variables:

```bash

export MLFLOW_TRACKING_URI=https://dagshub.com/buzaXnov/MLflow-Demo.mlflow

export MLFLOW_TRACKING_USERNAME=buzaXnov 

export MLFLOW_TRACKING_PASSWORD=c2f97b6e1897763abc2b78d3781adbbf30ba2026

```

## MLflow on AWS

### MLflow on AWS Setup

1. Login to AWS
2. Create IAM User  with AdministratorAccess
3. Export the credentials in your AWS CLI by running `aws configure`
4. Create an S3 bucket
5. Create an EC2 machine (Ubuntu) and add Security groups 5000 port

Run the following command on EC2 machine:

```bash
sudo apt update

sudo apt install python3-pip

# Depending on your version of Python on the EC2 instance
sudo apt install python3.12-venv

mkdir mlflow

cd mlflow

python3 -m venv .venv

source .venv/bin/activate

# To prevent the No module named 'pkg_resources' error (missing package)
pip install setuptools

pip install mlflow

pip install awscli

pip install boto3

# Then set aws credentials
aws configure

mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-bucket-filip

# open Public IPv4 DNS to the port 5000

# set uri in your local terminal and in your code
export MLFLOW_TRACKING_URI=http://ec2-54-227-42-110.compute-1.amazonaws.com:5000/
```