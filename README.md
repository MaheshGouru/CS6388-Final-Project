# CS6388 Mini-Project

## Overview
In this assignment we will a Petri Net for Mass-Spring-Dampers. Petri Nets are a formal, graphical, executable technique for the specification and analysis of concurrent, discrete-event dynamic systems.

## Manual Installation
First, install the myminiproject following:
- [NodeJS](https://nodejs.org/en/) (LTS recommended)
- [MongoDB](https://www.mongodb.com/)

Second, start mongodb locally by running the `mongod` executable in your mongodb installation (you may need to create a `data` directory or set `--dbpath`).

Then, run `webgme start` from the project root to start . Finally, navigate to `http://localhost:8888` to start using myminiproject!

### Dependencies
- Docker: sudo apt-get install openjdk-9-jre-headless
- WebGME: sudo apt-get install libtool

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