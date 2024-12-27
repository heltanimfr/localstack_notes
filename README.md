# LocalStack
Install localstack docker
> docker pull localstack/localstack

Launch docker : open port, mount points (/mnt/share will store the expected zip file)
> docker run --rm -p 4566:4566 -v /var/run/docker.sock:/var/run/docker.sock -v ${PWD}:/mnt/share/ localstack/localstack

# LocalStack Docker
Start docker from already executed docker container
> docker exec -it 0e5019579c33 /bin/bash

Create AWS lambda function w/ timeout, zip, hanlder, role & env variables settings
> awslocal lambda create-function --function-name originproxy \
--runtime python3.12 \
--timeout 60 \
--zip-file fileb://file.zip \
--handler hewmorigin_lambda.lambda_handler \
--role arn:aws:iam::000000000000:role/irrelevant \
--environment Variables="{ORIGIN_URL=https://c223d9abb67d57c7.mediapackage.eu-west-1.amazonaws.com}"

List registered AWS lambda functions
> awslocal lambda list-functions

Delete a specific AWS lambda function
> awslocal lambda delete-function --function-name originproxy

Call AWS lambda w/ a specific json event structure. Store output results in output.txt file
> awslocal lambda invoke --function-name originproxy \
--payload '{ "path":"/out/v1/a398a27b3926403ca9d0b02cfabd2b3b/index.m3u8", "queryStringParameters" : ""}' \
output.txt


# References
How to install localstack CLI : https://docs.localstack.cloud/getting-started/installation/
Localstack Auth token setup : https://docs.localstack.cloud/getting-started/auth-token/

