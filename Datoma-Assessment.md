# CHALLENGES:
Kubernetes Config Context
Python S3 Get Contents
Longest Increasing Sequence
Node.js Detailed Log Analysis
Docker Custom Redis

Challenge1: Docker Custom Redis

In the Bash script, write a program that creates a file named Dockerfile. The contents of the Dockerfile should have the following commands:

1. Set the base image to redis: 7.0.11 and expose port 6379.

3. Set the redis.conf file to use a custom configuration file named my_redis.conf from the current directory.

4. Set an environment variable named REDIS ENV with the value custom.

5. Create a directory named/data to be used as a Redis data directory.

6. Set the user to run the Redis server as redis.

Print the contents of your Dockerfile at the end.


Challenge 2: Python S3 Get Contents

In the Python file, write a program to access the contents of the bucket coderbytechallengesandbox. In there there might be multiple files, but your program should find the file with the prefix cb and then output the contents of that file. You should use the boto3 module to solve this challenge.

You do not need any access keys to access the bucket because it is public. This post might help you with how to access the bucket.

Example Output

contents of some file


Challenge 3: Kubernetes Config Context

In the Bash script, you will need to modify the configuration file and provide some clusters and context to it. Use the --kubeconfig flag and set it to a file named kube custom.config

With the CLI command config, first set 2 clusters with set-cluster. The first should be called "development", its--server should be set to "https://0.0.1.1" and the -certificate-authority should be set to "temp_ca_file" Then add another cluster similar to the one above, except it should be called "staging" and the server should be set to "https://5.6.7.8"

Then set 2 contexts, the first should be called "dev-frontend", the --cluser should be set to "development", the--namespace should be set to "frontend", and finally --user should be "developer". The second context should be similar to the one above, except it should be called "dev-staging" and it should be tied to the "staging" cluster.

Finally, print the contents of this config file.


Challenge 4 : Longest Increasing Sequence

Have the function

LongestIncreasingSequence (arr) take the array of positive integers stored in arr and return the length of the longest increasing subsequence (LIS). A LIS is a subset of the original list where the numbers are in sorted order, from lowest to highest, and are in increasing order. The sequence does not need to be contiguous or unique, and there can be several different subsequences. For example: if arr is [4, 3, 5, 1, 6) then a possible LIS is [3, 5, 6], and another is [1, 6]. For this input, your program should return 3 because that is the length of the longest increasing subsequence.

Examples

Input: [9, 9, 4, 2]

Output: 1

Input: [10, 22, 9, 33, 21, 50, 41, 60, 22, 68, 90]

Output: 7


Challenge 5 : Node.js Detailed Log Analysis

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



Question 1:
Imagine a developer reports that their newly deployed microservice, running in a Kubernetes pod, is healthy (the readiness and liveness probes are passing) and the logs look fine, but it cannot connect to the PostgreSQ
