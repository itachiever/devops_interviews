# Job Description: 

Title: DevOps Engineer

================================
1) Basic knowledge on Shell scripting / Python and Ansible playbooks
a) Execute the scripts/ playbook
b) Can independently can able to fix the issues in scrips / playbook
2) Hands on experience on Linux OS and Azure/AWS Cloud
3) Execution of CI/CD pipeline
3) Performing OS upgrade / rollback testing
4) Good debugging skills and ability the find the root cuase of the issue by analysing
Experience: 3-4 years

---

Project:- Motorola, Manayata Tech Park, Nagavara/Hebbal, Bengaluru.

 Developer/Devops engineer: (2 - 5yrs) 

================================

1) Basic knowledge on Shell scripting / Python and Ansible playbooks

a)         Execute the scripts/ playbook

b)         Can independently can able to fix the issues in scrips / playbook

2) Hands on experience on Linux OS and Azure/AWS Cloud

3) Execution of CI/CD pipeline

3) Performing OS upgrade / rollback testing

4) Good debugging skills and ability the find the root cuase of the issue by analysing


# Questions

1. Have you worked on Jenkins and Ansible? What kind of work have you done in Ansible?


2. What scripting languages have you worked with? What Python libraries have you used?


3. I need to deploy Telnet RPM on 50 servers, then start the Telnet service. Once started, I need to validate that the Telnet service is running and display a message accordingly. How would you do this?


4. How do you use tagging in Ansible? How do you use Ansible roles, and how do you control the execution time or order of roles?


5. Have you worked with Ansible Galaxy and dynamic inventory? How do you create a dynamic inventory?


6. In Jenkins, how do you use Shared Libraries?


7. Let’s say I logged into a Linux server with user "A", but I do not have the required permissions. What would you do to get the necessary permissions?


8. Write a Python program to find the largest and smallest numbers in an array using a single loop. How would you do this?


9. What load balancers have you worked with in your environment?

# Answers:




### **1. Jenkins and Ansible Experience**

**Q1. Have you worked on Jenkins and Ansible? What kind of work have you done in Ansible?**

**Answer:**
**Jenkins** is used for building CI/CD pipelines to automate the build, test, and deployment processes.
**Ansible** is used for Configuration Management and orchestration.
**Work done in Ansible:**
*   **Configuration Management:** Installing packages (Nginx, Java), managing services, and modifying configuration files on target servers.
*   **Deployment:** Deploying Java JAR files or Python applications to remote servers.
*   **Orchestration:** Coordinating multi-tier deployments, such as updating load balancers only after application servers are updated.
*   **Ad-hoc Commands:** Running quick commands across multiple servers simultaneously (e.g., checking disk space).

---

### **2. Scripting & Python Libraries**

**Q2. What scripting languages have you worked with? What Python libraries have you used?**

**Answer:**
The primary scripting languages are **Python** and **Bash**. Python is used for complex logic and API interactions, while Bash is used for system-level tasks.
**Common Python Libraries used in DevOps:**
*   **Boto3:** The AWS SDK for Python, used to automate AWS services like EC2, S3, and Lambda.
*   **Requests:** Used to make HTTP requests to interact with REST APIs (like Jenkins or GitLab APIs).
*   **Os & Sys:** Used for interacting with the operating system (file paths, environment variables).
*   **Jinja2:** Used for templating configuration files.

---

### **3. Scenario: Telnet Deployment & Validation**

**Q3. I need to deploy Telnet RPM on 50 servers, then start the Telnet service. Once started, I need to validate that the Telnet service is running and display a message accordingly. How would you do this?**

**Answer:**
This is efficiently handled using an **Ansible Playbook**.

**Steps:**
1.  **Inventory:** Create an inventory file listing the IP addresses of the 50 servers.
2.  **Playbook:**
    *   **Task 1 (Install):** Use the `yum` or `apt` module to install the Telnet package (`state: present`).
    *   **Task 2 (Start):** Use the `systemd` module to start and enable the service (`state: started`, `enabled: yes`).
    *   **Task 3 (Validate):** Use the `service_facts` module to gather the current status of services. Then, use a conditional check (`when`) to verify if `ansible_facts.services["telnet.service"].state` is "running".
    *   **Task 4 (Display):** Use the `debug` module to print a success message if the condition is met, or a failure message if it is not.

**Example Logic:**
```yaml
- name: Check Telnet Status
  service_facts:
- debug:
    msg: "Telnet is running successfully"
  when: ansible_facts.services["telnet.service"].state == "running"
```

---

### **4. Ansible Tagging, Roles & Execution**

**Q4. How do you use tagging in Ansible? How do you use Ansible roles, and how do you control the execution time or order of roles?**

**Answer:**
**Tagging:** Tags allow running specific parts of a playbook. We assign a tag to a task (e.g., `tags: ["install"]`). When running the playbook, we use `--tags "install"` to run only those tasks, skipping others.
**Roles:** Roles are a way to group related tasks, variables, files, and templates into a standardized directory structure. They promote reusability (e.g., a "Webserver" role can be reused across projects).
**Controlling Execution Order:**
1.  **`pre_tasks` and `post_tasks`:** We define tasks that must run *before* or *after* the roles in the main playbook.
2.  **Dependencies:** Inside a role's `meta/main.yml`, we can define dependencies (e.g., this "Java App" role requires the "Java" role to run first).
3.  **Order Control:** By default, Ansible runs tasks in the order they are written. For roles, we can control the execution order of the inventory using the `order: sorted` or `order: reverse_sorted` settings.

---

### **5. Ansible Galaxy & Dynamic Inventory**

**Q5. Have you worked with Ansible Galaxy and dynamic inventory? How do you create a dynamic inventory?**

**Answer:**
**Ansible Galaxy:** It is a repository for community-contributed roles. We use the `ansible-galaxy install <role-name>` command to download pre-written roles (e.g., installing Nginx) to use in our playbooks.
**Dynamic Inventory:** Unlike a static text file, dynamic inventory generates the list of target hosts on the fly by querying an external source (like AWS EC2, Azure, or vCenter).
**Creation:**
1.  We use a script (Python, Bash) provided by Ansible or the cloud provider (e.g., `ec2.py` or the AWS EC2 plugin).
2.  We configure the `ansible.cfg` file to point to this script.
3.  When we run a playbook, Ansible executes this script, queries the cloud API to get a list of running instances, and uses that list as the inventory.

---

### **6. Jenkins Shared Libraries**

**Q6. In Jenkins, how do you use Shared Libraries?**

**Answer:**
Jenkins Shared Libraries allow us to extract common pipeline logic into a shared repository, so it can be reused across multiple Jenkins jobs.
**Usage:**
1.  **Define Library:** We create a Git repo with Groovy code (functions/classes) and add it to Jenkins system configuration under "Global Libraries".
2.  **Import in Pipeline:** In the `Jenkinsfile`, we use `@Library('my-shared-lib') _` at the top to import it.
3.  **Call Functions:** We can now call the functions defined in that library directly in the pipeline stages. For example, calling a standard function `buildAndTest()` instead of writing the code for every project.

---

### **7. Linux Permissions Scenario**

**Q7. Let’s say I logged into a Linux server with user "A", but I do not have the required permissions. What would you do to get the necessary permissions?**

**Answer:**
If user "A" lacks permissions to perform a task (e.g., installing software or editing a config file), it means the user is not a root user or part of a privileged group.
**Steps to resolve:**
1.  **Check Groups:** Verify if the user belongs to necessary groups (like `wheel` or `sudo`) using the `id` or `groups` command.
2.  **Sudo Access:** Attempt to use the `sudo` command (e.g., `sudo yum install package`). If the user is not in the sudoers file, contact the System Administrator.
3.  **Add to Sudoers:** The administrator can edit the `/etc/sudoers` file (using `visudo`) and grant user "A" sudo privileges by adding the line `username ALL=(ALL) ALL`.
4.  **Switch User:** Alternatively, switch to the `root` user using `su -` or `sudo -i` if the password is known.

---

### **8. Python Coding Question (Min/Max)**

**Q8. Write a Python program to find the largest and smallest numbers in an array using a single loop. How would you do this, also explain?**

**Answer:**
**The Code:**
```python
def find_min_max(arr):
    if not arr:
        return None, None

    # Initialize min and max with the first element
    min_val = arr[0]
    max_val = arr[0]

    # Loop through the array starting from the second element
    for num in arr[1:]:
        if num < min_val:
            min_val = num
        if num > max_val:
            max_val = num

    return min_val, max_val

# Example usage
numbers = [12, 4, 56, 2, 89, 3]
min_val, max_val = find_min_max(numbers)
print(f"Smallest: {min_val}, Largest: {max_val}")
```
**Explanation:**
Instead of using Python's built-in `min()` and `max()` functions (which iterate twice), we use a single `for` loop.
1.  We initialize both `min_val` and `max_val` to the first element of the array.
2.  As we iterate through the rest of the numbers, we compare each number with the current `min_val` and `max_val`.
3.  If a number is smaller than `min_val`, we update `min_val`. If it is larger than `max_val`, we update `max_val`.
This approach is efficient (Time Complexity: O(n)) as it traverses the list only once.

---

### **9. Load Balancers**

**Q9. What load balancers have you worked with in your environment?**

**Answer:**
Load balancers are categorized into **Layer 4** and **Layer 7**.
*   **AWS Application Load Balancer (ALB):** Works at Layer 7 (HTTP/HTTPS). It routes traffic based on URL paths (e.g., `/api` to one service, `/images` to another).
*   **AWS Network Load Balancer (NLB):** Works at Layer 4 (TCP/UDP). It handles millions of requests per second with ultra-low latency, ideal for TCP traffic.
*   **Nginx:** An open-source Load Balancer and Web Server often used inside Kubernetes clusters as an Ingress Controller or on-premise servers.
*   **HAProxy:** Another popular open-source load balancer known for high performance and reliability.
