# Nginx with Self-Signed SSL Configuration Guide

The purpose of this project is to set up a local server using Nginx and SSL certificates. I will configure Nginx for two static websites - one on HTTP and the other on HTTPS. I will also set up HTTP Basic Auth for the first site using the apache2-utils package. I will configure a self-signed SSL certificate for the second site using OpenSSL. Additionally, I will set up an HTTP to HTTPS redirect from Site1 to Site2.

## 1. Checking Nginx Installation and Status

![Nginx Service Status](./active-nginx-process.png)

Verifying Nginx service status with `systemctl status nginx` command. The service is active (running) with master process PID 7140.

## 2. Testing Nginx with curl

![Testing Nginx with curl](./check-nginx-with-curl.png)

Using `curl localhost` to test the default Nginx welcome page.

## 3. Viewing Default Page in Browser

![Nginx Welcome Page in Browser](./check-in-browser.png)

Default Nginx welcome page displayed in a web browser, confirming successful installation.

## 4. Configuring Local DNS with Hosts File

![Updating /etc/hosts](./add-content-to-etc-hosts.png)

Adding local domain entries to the hosts file for local development.

![Current /etc/hosts Contents](./content-of-etc-hosts.png)

Here we'll add local domains for development by modifying the /etc/hosts file so that site1.local and site2.local point to the local host.

## 5. Accessing Nginx Configuration Directory

![Nginx Configuration Files](./cd-to-nginx-catalog.png)

Listing contents of the main Nginx configuration directory at `/etc/nginx/` showing all available configuration files and directories.

## 6. Creating Website Content

![Editing index.html](./create-content-of-indexhtml.png)

Creating and editing the main `index.html` file for the website content.

## 7. Creating Nginx Configuration Files

![Creating Configuration Files](./create-conf-files.png)

Using `nano` to create and edit Nginx configuration files in the sites-available directory. We'll do everything in conf.d as it's the standard location for configurations in Nginx.

### Site 1 Configuration

![Site 1 Virtual Host Setup](./setup-site1-conf.png)

Creating the first virtual host configuration file for site1 in the `/etc/nginx/sites-available/` directory.

### Site 2 Configuration

Creating the second virtual host configuration is similar to the first one, but with the following adjustments:

- Different server name (site2.local)

## 8. Verifying Nginx Configuration

![Nginx Configuration Test](./make-sure-conf-ok.png)

Running `nginx -t` to test the Nginx configuration files for correct syntax.

After verifying the configuration, we need to reload Nginx to apply the changes.

![Reloading Nginx](./reload-nginx-after-conf.png)

## 9. Viewing Website Results

### Site 1 Result

![Site 1 Live View](./site1-result.png)

Successfully loaded site1 with the custom content in the web browser.

### Site 2 Result

![Site 2 Live View](./site2-result.png)

Successfully loaded site2 with the custom content in the web browser.

## 10. Implementing Basic Authentication

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

## 11. Setting Up SSL with Self-Signed Certificate

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

## 12. Configuring HTTP to HTTPS Redirect

![HTTP to HTTPS Redirect Setup](./update-conf-site-1-reverse-proxy.png)

![HTTP to HTTPS Redirect Setup](./update-conf-site-2-reverse-proxy.png)

Configuring Nginx to automatically redirect HTTP traffic to HTTPS for secure connections.

Now when accessing http://site1.local, we should be redirected to https://site2.local - everything is working successfully.

## 13. Monitoring Nginx Processes

![Nginx Process List](./processes.png)

Viewing all running Nginx processes to ensure everything is working correctly.
