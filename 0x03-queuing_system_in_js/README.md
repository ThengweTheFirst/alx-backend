# 0x03. Queuing System in JS

## Description
This project focuses on building a queuing system using Node.js, Redis, and the Kue library. The queuing system allows for the management of background jobs using Redis as the storage mechanism and Kue as the job queue. The project covers various aspects of creating, processing, and tracking jobs within the queuing system.

## Table of Contents
- [Background](#background)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Tasks](#tasks)
  - [Task 0: Install a Redis Instance](#task-0-install-a-redis-instance)
  - [Task 1: Node Redis Client](#task-1-node-redis-client)
  - [Task 2: Node Redis Client and Basic Operations](#task-2-node-redis-client-and-basic-operations)
  - [Task 3: Node Redis Client and Async Operations](#task-3-node-redis-client-and-async-operations)
  - [Task 4: Node Redis Client and Advanced Operations](#task-4-node-redis-client-and-advanced-operations)
  - [Task 5: Node Redis Client Publisher and Subscriber](#task-5-node-redis-client-publisher-and-subscriber)
  - [Task 6: Create the Job Creator](#task-6-create-the-job-creator)
  - [Task 7: Create the Job Processor](#task-7-create-the-job-processor)
  - [Task 8: Track Progress and Errors with Kue: Create the Job Creator](#task-8-track-progress-and-errors-with-kue-create-the-job-creator)
  - [Task 9: Track Progress and Errors with Kue: Create the Job Processor](#task-9-track-progress-and-errors-with-kue-create-the-job-processor)
  - [Task 10: Writing the Job Creation Function](#task-10-writing-the-job-creation-function)
  - [Task 11: Writing the Test for Job Creation](#task-11-writing-the-test-for-job-creation)
  - [Task 12: In Stock?](#task-12-in-stock)
  - [Task 13: Can I Have a Seat?](#task-13-can-i-have-a-seat)

## Background
This project focuses on creating a queuing system using Node.js, Redis, and the Kue library. The queuing system allows for the efficient management of background jobs and tasks, which can be processed asynchronously. Redis serves as the storage mechanism for job data, and Kue facilitates the creation, processing, and management of jobs in a scalable manner.

## Learning Objectives
Upon completing this project, participants will be able to:

- Set up and run a Redis server on a local machine.
- Use the Redis client interface for basic operations.
- Utilize Node.js and Redis to perform asynchronous operations.
- Implement advanced Redis operations, including storing hash values.
- Create a publisher-subscriber system using Redis for inter-process communication.
- Build a queuing system using Kue to manage background jobs.
- Develop scripts to interact with the Redis-based queuing system.
- Write tests for job creation and processing using Mocha.

## Requirements
- Ubuntu 18.04
- Node.js 12.x
- Redis 5.0.7

## Installation
1. Install the latest stable Redis version:
```bash
$ wget http://download.redis.io/releases/redis-6.0.10.tar.gz
$ tar xzf redis-6.0.10.tar.gz
$ cd redis-6.0.10
$ make
```

2. Start Redis in the background:
```bash
$ src/redis-server &
```

3. Verify Redis server is working:
```bash
$ src/redis-cli ping
```

4. Install required dependencies for Node.js scripts:
```bash
$ npm install
```

## Usage
To run the various tasks and scripts, use the following command:
```bash
$ npm run dev <script-file>
```

## Tasks
### Task 0: Install a Redis Instance
- Download, extract, and compile the latest stable Redis version.
- Start Redis server in the background.
- Verify the server is working and set values in Redis.

### Task 1: Node Redis Client
- Create a Node.js script that connects to the Redis server using the Redis client interface.
- Log connection status and errors to the console.

### Task 2: Node Redis Client and Basic Operations
- Expand the Node.js script to perform basic operations like setting and retrieving values from Redis.
- Create functions for setting and displaying values in Redis.

### Task 3: Node Redis Client and Async Operations
- Modify the script to handle asynchronous operations using `promisify`.
- Use `async/await` to interact with Redis asynchronously.

### Task 4: Node Redis Client and Advanced Operations
- Store hash values in

 Redis using the script.
- Implement functions to set, retrieve, and display hash values.

### Task 5: Node Redis Client Publisher and Subscriber
- Create a publisher script that publishes messages to a channel.
- Implement a subscriber script that subscribes to the channel and receives messages.

### Task 6: Create the Job Creator
- Set up Kue and create a job creator script.
- Define a job creation function and enqueue jobs using Kue.

### Task 7: Create the Job Processor
- Develop a job processor script to process jobs created by Kue.
- Implement a function to process jobs and log job details.

### Task 8: Track Progress and Errors with Kue: Create the Job Creator
- Enhance the job creator to track job progress and handle errors.
- Update the job creation function to report progress and errors.

### Task 9: Track Progress and Errors with Kue: Create the Job Processor
- Modify the job processor to handle progress and errors from jobs.
- Implement functions to update job progress and handle job failures.

### Task 10: Writing the Job Creation Function
- Implement the main job creation function with advanced features.
- Create jobs with different priority levels and delay times.

### Task 11: Writing the Test for Job Creation
- Set up Mocha and Chai for testing.
- Write tests to ensure the job creation function works as expected.

### Task 12: In Stock?
- Develop a function to check and update product stock using Redis and Kue.
- Create a job to process the stock check and update.

### Task 13: Can I Have a Seat?
- Implement a function to check seat availability using Redis and Kue.
- Create a job to process seat availability requests.

---

