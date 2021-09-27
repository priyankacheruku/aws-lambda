# aws-lambda
AWS Lambda with custom docker images as runtime

## Commands
To build docker image

    docker build -t docker-lambda .
    
To run the image

    docker run -d -p 8080:8080 docker-lambda

to test it using `curl` 

    curl -XPOST "http://localhost:8080/2015-03-31/functions/function/invocations" -d '{"payload":"hello world!"}'


## docker configurations for lambda handler need to know

 * Base image need to be from public ecr.
 * LAMBDA_TASK_ROOT – The path to your Lambda function code.
 * var/tasks/ is the working directory default .
 * requirements need to be at installed with target.
 * Default it exports 8080 port.
 * we can only invoke one handler(function) need to mention that at the end ["app.handler"].
 * handler accepts two arguments `event` has payload and `context` for extra information 
