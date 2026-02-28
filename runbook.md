# Runbook — EC2 Public Web Demo

## 1. Provisioning
- **AMI:** Amazon Linux 2023
- **Type:** t3.micro
- **Security Group:** - Port 80 (HTTP) -> 0.0.0.0/0
  - Port 22 (SSH) -> My IP

## 2. Server Configuration
Connect via SSH and execute the following:
```bash
# Update and install Nginx
sudo dnf update -y
sudo dnf install -y nginx

# Start and enable the service
sudo systemctl enable --now nginx

# Verify the service is active
sudo systemctl status nginx

sudo tee /usr/share/nginx/html/index.html > /dev/null <<'HTML'
<!DOCTYPE html>
<html>
<head>
    <title>Success - Portfolio Demo</title>
</head>
<body style="font-family: Arial, sans-serif; margin: 40px;">
    <h1>AWS EC2 Deployment Verified</h1>
    <p><strong>Status:</strong> Nginx is successfully running on Amazon Linux 
2023.</p>
    <p>This page demonstrates successful web server provisioning and security group 
configuration.</p>
</body>
</html>
HTML
