# CHALLENGES:
* Kubernetes Config Context
* Python S3 Get Contents
* Longest Increasing Sequence
* Node.js Detailed Log Analysis
* Docker Custom Redis

# Challenge1: Docker Custom Redis

In the Bash script, write a program that creates a file named Dockerfile. The contents of the Dockerfile should have the following commands:

1. Set the base image to redis: 7.0.11 and expose port 6379.

3. Set the redis.conf file to use a custom configuration file named my_redis.conf from the current directory.

4. Set an environment variable named REDIS ENV with the value custom.

5. Create a directory named/data to be used as a Redis data directory.

6. Set the user to run the Redis server as redis.

Print the contents of your Dockerfile at the end.


# Challenge 2: Python S3 Get Contents

In the Python file, write a program to access the contents of the bucket coderbytechallengesandbox. In there there might be multiple files, but your program should find the file with the prefix cb and then output the contents of that file. You should use the boto3 module to solve this challenge.

You do not need any access keys to access the bucket because it is public. This post might help you with how to access the bucket.

Example Output

contents of some file


# Challenge 3: Kubernetes Config Context

In the Bash script, you will need to modify the configuration file and provide some clusters and context to it. Use the --kubeconfig flag and set it to a file named kube custom.config

With the CLI command config, first set 2 clusters with set-cluster. The first should be called "development", its--server should be set to "https://0.0.1.1" and the -certificate-authority should be set to "temp_ca_file" Then add another cluster similar to the one above, except it should be called "staging" and the server should be set to "https://5.6.7.8"

Then set 2 contexts, the first should be called "dev-frontend", the --cluser should be set to "development", the--namespace should be set to "frontend", and finally --user should be "developer". The second context should be similar to the one above, except it should be called "dev-staging" and it should be tied to the "staging" cluster.

Finally, print the contents of this config file.


# Challenge 4 : Longest Increasing Sequence

Have the function

LongestIncreasingSequence (arr) take the array of positive integers stored in arr and return the length of the longest increasing subsequence (LIS). A LIS is a subset of the original list where the numbers are in sorted order, from lowest to highest, and are in increasing order. The sequence does not need to be contiguous or unique, and there can be several different subsequences. For example: if arr is [4, 3, 5, 1, 6) then a possible LIS is [3, 5, 6], and another is [1, 6]. For this input, your program should return 3 because that is the length of the longest increasing subsequence.

Examples

Input: [9, 9, 4, 2]

Output: 1

Input: [10, 22, 9, 33, 21, 50, 41, 60, 22, 68, 90]

Output: 7


# Challenge 5 : Node.js Detailed Log Analysis

In the JavaScript file, write a program to perform a GET request on the route https://coderbyte.com/api/challenges/logs/web-logs-raw and then parse the raw web server logs. Each line begins with a date, e.g., Apr 10 11:17:35. Your program should do the following:

1. Loop through each log entry and find the lines that contain the string "coderbyte heroku/router". Ignore log entries where the 'status' is not 200.

2. For each of those extract the 'request_id', 'method', 'path', `status`, `response_time', 'dyno', and 'connect_time' values.

3. Group the log entries by 'dyno' and calculate the following for each 'dyno':

- Total number of requests.

- Average response time.

- Maximum connect time.

4. Output the results in the following format:

dyno: total_requests, average_response_time ms,
max_connect_time ms


# Questions:

* Question 1:

Imagine a developer reports that their newly deployed microservice, running in a Kubernetes pod, is healthy (the readiness and liveness probes are passing) and the logs look fine, but it cannot connect to the PostgreSQL database running in a different pod within the same namespace.

Walk me through, step-by-step, how you would troubleshoot this network connectivity issue from your command line. What are the most likely culprits in the order you would investigate them?

* Question 2 :
Tell me about the most memorable or challenging production outage you were directly involved in resolving. I'm not interested in the simple ones. I want to hear about one where the cause was not immediately obvious and the standard monitoring dashboards weren't helping.

What was the user-facing symptom? What was your initial hypothesis and how did you prove or disprove it? What was the actual root cause, and what long-term changes did you implement to prevent it from ever happening again?

* Question 3:
A critical Linux server running one of our applications is reported to be 'slow. You ssh in and run top. You see that the CPU usage is very low (under 20%) and there is plenty of free memory. However, the load average is unusually high.

What does this combination of symptoms (low CPU, high load average, free RAM) suggest to you? What specific command-line tools would you use next to diagnose the bottleneck, and what are you looking for?

* Question 4:
We have a critical data pipeline: microservices write events to a Kafka topic, and a consumer service reads from that topic to write data into our ClickHouse database. A data analyst reports that the dashboards are showing a significant drop in event volume for the last hour.

The microservice producers are reporting no errors, and the Kafka brokers seem healthy. How do you debug this potential data loss or delay? What is the single most important metric you would check first, and what tools would you use?


* Question 5:
What are your short-term professional goals, and how do you plan to achieve them?
