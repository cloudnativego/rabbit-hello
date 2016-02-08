# RabbitMQ Hello World
This is not a code sample in the traditional sense that it isn't really designed to teach you much.
The code in `send.go` and `receive.go` is taken almost line-for-line from the RabbitMQ Tutorials in their documentation.
We have modified the address so it points to a default docker-machine IP. To figure out our own docker-machine IP, use:

`docker-machine ip default` (or replace `default` with the name of your Docker machine).

Next, you can fire up a RabbitMQ Docker machine so you don't have to clutter your machine with a complicated install.
To run RabbitMQ, use the following command:

`docker run -d --hostname my-rabbit --name some-rabbit -p 8080:15672 -p 4369:4369 -p 5672:5672 rabbitmq:3-management`

This creates a docker container named **some-rabbit**. According to the docs from RabbitMQ, you are likely to run into odd issues if you don't name your containers something specific.

Before you run the code samples, make sure your local Go workspace has a copy of the **amqp** dependency:

`go get github.com/streadway/amqp`

Once docker is running, you can use the following command to send a message via RabbitMQ:

`go run send.go`

and to receive a message:

`go run receive.go`
