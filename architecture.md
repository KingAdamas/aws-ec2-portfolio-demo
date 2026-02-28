# Architecture — EC2 Public Web Demo

## System Components
- **Client Browser:** Accesses the demo page over standard HTTP.
- **AWS Security Group (Firewall):** - **Inbound:** Permits TCP Port 80 (HTTP) from 
`0.0.0.0/0` and TCP Port 22 (SSH) from `My IP` only.
  - **Outbound:** Allows all traffic (default) for package updates and Nginx 
installation.
- **EC2 Instance (Amazon Linux 2023):** The compute resource hosting the web server.
- **Nginx:** The high-performance web server software serving the static HTML 
content.
- **EBS Root Volume:** 8GB General Purpose SSD (gp3) providing the OS and file 
storage.

## Traffic Flow
1. **Request:** A user enters the Public IPv4 address of the instance into their 
browser.
2. **Filtering:** The AWS Security Group evaluates the request. Since it is on Port 
80, it is permitted.
3. **Processing:** The request reaches the Nginx service running on the Amazon Linux 
OS.
4. **Response:** Nginx retrieves the `index.html` file from `/usr/share/nginx/html/` 
and serves it back to the user.

## Lifecycle Management
- **Provisioning:** Manual via AWS Console (demonstrates UI proficiency).
- **Configuration:** Bash-based installation and service enablement.
- **Termination:** Resource destroyed after verification to ensure 100% cost control.
