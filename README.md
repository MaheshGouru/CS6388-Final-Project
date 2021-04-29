# CS6381 Mini-Project

## Overview
In this assignment we will build upon the PUB/SUB middleware from Assignment 2. 
We support ownership strength for fidelity in publishing and acquisition of recent events through message buffers. 
With ownership strength, information from only the highest ownership strength publisher gets relayed to the subscriber. 
As for the the history quality of service, we will require that last N samples of information published on a topic be preserved in a sliding window fashion.

| Simple Broker Latency                                                                                                    | Complex Broker Latency                                                                                                     | Simple Flooding Latency                                                                                                      | Complex Flooding Latency                                                                                                       |
|--------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| ![simple_broker](https://github.com/edmasters/single_broker_pub_sub/blob/automated-local-host/results/simple_broker.png) | ![complex_broker](https://github.com/edmasters/single_broker_pub_sub/blob/automated-local-host/results/complex_broker.png) | ![simple flooding](https://github.com/edmasters/single_broker_pub_sub/blob/automated-local-host/results/simple_flooding.png) | ![complex flooding](https://github.com/edmasters/single_broker_pub_sub/blob/automated-local-host/results/complex_flooding.png) |

## Manual Installation
First, install the myminiproject following:
- [NodeJS](https://nodejs.org/en/) (LTS recommended)
- [MongoDB](https://www.mongodb.com/)

Second, start mongodb locally by running the `mongod` executable in your mongodb installation (you may need to create a `data` directory or set `--dbpath`).

Then, run `webgme start` from the project root to start . Finally, navigate to `http://localhost:8888` to start using myminiproject!

### Dependencies
- Java: sudo apt-get install openjdk-9-jre-headless
- libtools: sudo apt-get install libtool
- Zookeeper: http://www.gtlib.gatech.edu/pub/apache/zookeeper/ <br/>
      -Uncompress: tar xvzf zookeeper-'version'.tar.gz
- Kazoo: pip install python3 Kazoo

## Before running the scripts

## Start the WebGME Server

To build and launch (first time):
```bash
$ docker-compose up -d
```
To create new images (--no-cache) to force building from scratch:
```bash
$ docker-compose build
```
To launch again (leave out -d for non daemon launch):
```bash
$ docker-compose up -d
```
Short command for rebuilding and restarting
```bash
$ docker-compose up -d --build
```
To stop containers:
```bash
$ docker-compose stop
```
To clean up containers/images/networks:
```bash
$ docker system prune
```

## Mininet Emulation
Assign the various hosts as either publisher or subscriber. 
Subsequently, passing the parameters for the stock ticker and API method will generate the connections.
The latencies will be exported to a csv and an analysis can be replicated with offline_analysis.py

### Simple Broker Approach
```bash
sudo mn -c #For cleaning up the environment
sudo mn --topo single,4 -x
mininet> h1 python3 ./middleware/broker.py &
mininet> h2 python3 ./middleware/subscriber.py AAPL True &
mininet> h3 python3 ./middleware/listener.py True &
mininet> h4 python3 ./middleware/publisher.py 1 AAPL True &
```