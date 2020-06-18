# How to build the docker image and push to ECR
1. Execute the following command to grant the ops privilege
```
aws-vault exec mediot-infra --duration=1h
```

2. Execute the following command to login to ECR
```
eval $(aws ecr get-login --no-include-email | sed 's|https://||g')
```

3. Execute the following command to build the docker image and tag the image
```
docker build -f Dockerfile \
    -t ${ECR_ENDPOINT}/aws-cli:latest \
    -t ${ECR_ENDPOINT}/aws-cli:2.0.22-mediot .
```

4. Execute the following command to push to ECR
```
docker push ${ECR_ENDPOINT}/aws-cli:latest
docker push ${ECR_ENDPOINT}/aws-cli:2.0.22-mediot
```
