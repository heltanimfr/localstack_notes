# LocalStack
Install localstack docker
> docker pull localstack/localstack
> docker run --rm -p 4566:4566 -v /var/run/docker.sock:/var/run/docker.sock localstack/localstack

# DOCKER
> docker exec -it 0e5019579c33 /bin/bash
> 
> awslocal lambda create-function --function-name originproxy \
--runtime python3.12 \
--timeout 60 \
--zip-file fileb://hewm.zip \
--handler hewmorigin_lambda.lambda_handler \
--role arn:aws:iam::000000000000:role/irrelevant \
--environment Variables="{ORIGIN_URL=https://c223d9abb67d57c7.mediapackage.eu-west-1.amazonaws.com}"

> awslocal lambda list-functions
> awslocal lambda delete-function --function-name originproxy
> awslocal lambda invoke --function-name originproxy \
--payload '{ "path":"/out/v1/a398a27b3926403ca9d0b02cfabd2b3b/index.m3u8", "queryStringParameters" : ""}' \
output.txt
