# Nginx with Self-Signed SSL Configuration Guide

## 1. Setting Up Local Development Environment

### Configuring Local DNS with Hosts File

#### Viewing Current Hosts File

![Current /etc/hosts Contents](./content-of-etc-hosts.png)

Displaying the current contents of the system's hosts file.

#### Adding Local Domains to Hosts File

![Updating /etc/hosts](./add-content-to-etc-hosts.png)

Adding local domain entries to the hosts file for local development.

## 2. Creating Nginx Configuration Files

![Creating Configuration Files](./create-conf-files.png)

Using `nano` to create and edit Nginx configuration files in the sites-available directory.

## 3. Checking Nginx Installation and Status

![Nginx Service Status](./active-nginx-process.png)

Verifying Nginx service status with `systemctl status nginx` command. The service is active (running) with master process PID 7140.

## 2. Accessing Nginx Configuration Directory

![Nginx Configuration Files](./cd-to-nginx-catalog.png)

Listing contents of the main Nginx configuration directory at `/etc/nginx/` showing all available configuration files and directories.

## 3. Testing Nginx with curl

![Testing Nginx with curl](./check-nginx-with-curl.png)

Using `curl localhost` to test the default Nginx welcome page.

## 4. Viewing Default Page in Browser

![Nginx Welcome Page in Browser](./check-in-browser.png)

Default Nginx welcome page displayed in a web browser, confirming successful installation.

## 5. Configuring Virtual Hosts

### Site 1 Configuration

![Site 1 Virtual Host Setup](./setup-site1-conf.png)

Creating the first virtual host configuration file for site1 in the `/etc/nginx/sites-available/` directory.

### Site 2 Configuration

![Site 2 Virtual Host Configuration](./update-conf-site-2-reverse-proxy.png)

Configuring the second virtual host (site2) similar to site1 with the following adjustments:
- Different server name (site2.local)
- Separate document root directory

## 6. Verifying Nginx Configuration

![Nginx Configuration Test](./make-sure-conf-ok.png)

Running `nginx -t` to test the Nginx configuration files for correct syntax.

## 7. Creating Website Content

![Editing index.html](./create-content-of-indexhtml.png)

Creating and editing the main `index.html` file for the website content.

## 8. Viewing Website Results

### Site 1 Result

![Site 1 Live View](./site1-result.png)

Successfully loaded site1 with the custom content in the web browser.

### Site 2 Result

![Site 2 Live View](./site2-result.png)

Successfully loaded site2 with the custom content in the web browser.

## 9. Implementing Basic Authentication

### Installing Apache2 Utilities

![Installing Apache2 Utils](./install-apatch2-for-auth.png)

Installing Apache2 utilities package to access the `htpasswd` tool for creating password files.

### Creating Authentication Password

![Creating Password File](./set-password.png)

Using `htpasswd` command to create a password file for HTTP basic authentication.

### Updating Site 1 Configuration with Authentication

![Adding Authentication to Nginx Config](./update-site1-conf-with-auth.png)

Modifying the site1 Nginx configuration to enable HTTP basic authentication.


### Testing Authentication in Browser

![Browser Authentication Prompt](./password-brawser-demo.png)

Browser displaying the authentication dialog when accessing the protected site.


### Verifying Password File

![Password File Contents](./passwd-res.png)

Displaying the contents of the created password file with the hashed credentials.


## 10. Setting Up SSL with Self-Signed Certificate

### Generating SSL Certificate

![SSL Certificate Generation](./setting-up-ssl-1.png)

Using OpenSSL to generate a self-signed SSL certificate for secure HTTPS connections.

### Configuring SSL Certificate

![SSL Certificate Configuration](./set-up-ssl-2.png)

Setting up the SSL certificate and private key paths in the Nginx configuration.

### Updating Site 2 with SSL

![Site 2 SSL Configuration](./update-site-2-ssl-config-with-ssl.png)

Modifying site2 configuration to enable HTTPS with the generated SSL certificate.

### Verifying SSL in Browser

![SSL Certificate Warning](./check-sertification-self-signed-in-browser.png)

Browser security warning for the self-signed certificate, which is expected behavior.

## 12. Monitoring Nginx Processes

![Nginx Process List](./processes.png)

Viewing all running Nginx processes

## 13. Applying Configuration Changes

![Reloading Nginx](./reload-nginx-after-conf.png)

Using `systemctl reload nginx` to apply configuration changes without downtime.

## 15. Configuring HTTP to HTTPS Redirect

![HTTP to HTTPS Redirect Setup](./update-conf-site-1-reverse-proxy.png)

Configuring Nginx to automatically redirect HTTP traffic to HTTPS for secure connections.
