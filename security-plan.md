# Cloud Architecture and Security Plan
Users 
 ↓ 
CDN 
 ↓ 
Load Balancer 
 ↓ 
Application Servers 
 ↓ 
Private Database 


## CDN 
The CDN stores cached copies of static content closer to users to improve loading speed.
Secure Cloud Architecture Using GitHub 
Cloud Computing Practical Activity | Student Version
## Load Balancer 
The load balancer distributes incoming requests across multiple application servers.
## Application Servers 
Application servers process requests from users. These servers should be placed in a private subnet. 
## Database 
The database stores student records. The database should remain private and should not be directly accessible from the Internet. 


# Public and Private Resources 
CDN	(Public)
	Delivers website files like images, CSS, and JavaScript to users over the internet.
Load Balancer	(Private)
	Distributes incoming requests between application servers and is usually protected from direct public access.
Application Server	(Private)
	Processes the application's requests and contains the main application logic.
Database	(Private)
	Stores student information and should only be accessible by authorized application servers.


# Security Controls 
IAM	
    Only authorized administrators, developers, and staff should have access to the cloud environment. Each user should have only the permissions needed for their role.
MFA	
    Administrator, developer, and other accounts with access to important cloud resources should use Multi-Factor Authentication to provide extra security.
Firewall / Security Group
	Only necessary connections should be allowed. Internet → Load Balancer = Allowed; Load Balancer → Application Server = Allowed; Application Server → Database = Allowed; Internet → Database = Blocked.
Encryption
	Student information should be encrypted to protect personal data such as names, student numbers, and email addresses from unauthorized access.
Logging
	Login attempts, changes to student records, database access, administrator actions, and security events should be recorded for auditing and troubleshooting.
Monitoring
	Suspicious login attempts, unusual traffic, repeated failed logins, unexpected database access, and other unusual activities should be monitored.
Backup
	The database should have regular backups so student records can be restored after accidental deletion, system failure, or other data loss.


# Principle of Least Privilege
Administrator	
    Full access to student records, user accounts, system settings, and reports.
Instructor
	Access to student records, grades, attendance, and class information.
Student
	Access only to their own profile, grades, attendance, and academic information.
Developer
	Access to application code, system configuration, and development tools, but not student data unless authorized.


# Shared Responsibility Model 
Physical data center	    Cloud Provider
Physical servers	        Cloud Provider
User accounts	            Customer
Student data	            Customer
IAM permissions         	Customer
Application security	    Customer
Database access rules	    Customer
Backups	                    Customer


1. What does Security OF the Cloud mean?

Security OF the Cloud refers to the security of the cloud provider's infrastructure, such as physical data centers, servers, networking, and hardware.

2. What does Security IN the Cloud mean?

Security IN the Cloud refers to the customer's responsibility for protecting their applications, accounts, data, permissions, databases, and other resources stored in the cloud.

3. **Which resource should be directly accessible from the Internet?**
   The **Load Balancer** should be directly accessible from the Internet because it receives user requests and sends them to the application servers.

4. **Why should the database remain private?**
   The database should remain private to protect sensitive student information from unauthorized access.

5. **Why should users not connect directly to the database?**
   Users should not connect directly to the database because it could expose sensitive data and create security risks. Users should access data through the application.

6. **What is the purpose of a load balancer?**
   A load balancer distributes incoming requests across multiple application servers to improve performance and reliability.

7. **What happens if one application server fails?**
   The load balancer sends requests to the other working application servers, so the system can continue operating.

8. **What is the purpose of a CDN?**
   A CDN delivers website files such as images, CSS, and JavaScript from servers closer to users, making the website load faster.

9. **Why should administrator accounts use MFA?**
   MFA adds an extra layer of security, making it harder for someone to access an administrator account even if the password is stolen.

10. **Why should administrator access not be given to every employee?**
    Giving everyone administrator access increases the risk of unauthorized changes, data loss, or security breaches.

11. **Why are logging and monitoring important?**
    They help detect suspicious activity, track system changes, identify problems, and investigate security incidents.

12. **Why are backups important?**
    Backups allow the database and student information to be restored if data is accidentally deleted, corrupted, or lost.
