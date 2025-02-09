# TP Docker

This application is a DockerCoin miner! 💰🐳📦🚢

No, you can't buy coffee with DockerCoins

How DockerCoins works:

 - worker asks to rng to give it random bytes
 - worker feeds those random bytes into hasher
 - each hash starting with 0 is a DockerCoin
 - DockerCoins are stored in redis
 - redis is also updated every second to track speed
 - you can see the progress with the webui !

## First part

 Create a Dockerfile for each of the 4 directory.

 Hint:
  - For *hasher*, this is a Ruby application, listening on port 80. The apps require to have sinatra and rackup and puma Ruby libraries , installed through gem command line.
  - For *rng*, this is a Python app that only require Flask library, installed through pip command line, and also listening on port 80.
  - For *webui*, this is a Node JS app, that require express and redis (version 3) libraries, installed trough npm command line, and also listening on port 80.
  - For *worker*, this is a Python app that require redis and requests libraries, installed through pip command line. This app does not expose any port.

You should now have enough information to write the 4 Dockerfiles.

Validate that you can build the 4 container images, and you can run them separately.

# Second part

You are now asked to create the *docker-compose.yml* file to be able to launch the full application, with only one command.

The app is composed of the 4 container images you have created in the first part and also a redis database where you can use the official redis image.

Try to stay simple and reduce to the strict minimum the number of commands used in the *docker-compose.yml*.

The webui should be exposed to port 8000 on your linux VM.

At the end of this part you should be able to connect to the webui and display some graph of performance of the dockercoins mining.

Hint: To connect to the webui from your laptop, use SSH Local port forwarding with -L8000:0.0.0.0:8000

# Bonus part

Take note of the performance of the app as base performance.

Try to scale the worker to 10 replicas, look at the performance increase and try to understand why the performance is not 10 times the base performance.

Try to fix the issue and validate that now the performance is closer to 10 times the base performance.


