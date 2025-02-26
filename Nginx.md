# Nginx Complete Guide

## Installing Nginx

### Linux (Ubuntu/Debian)

```sh
sudo apt update
sudo apt install nginx
```

### macOS (Using Homebrew)

```sh
brew install nginx
```

### Windows (Not Recommended for Production)

Nginx supports Windows, but it is not optimized for it. Some features may not work as expected.

1. Download the latest Windows version from: http\://nginx.org/en/download.html
2. Extract the ZIP file to `C:\nginx`
3. Open Command Prompt, navigate to the directory:
   ```sh
   cd C:\nginx
   ```
4. Start Nginx:
   ```sh
   nginx.exe
   ```
5. To stop Nginx:
   ```sh
   nginx -s stop
   ```

---

## Basic Nginx Commands

```sh
sudo systemctl start nginx   # Start Nginx
sudo systemctl stop nginx    # Stop Nginx
sudo systemctl restart nginx # Restart Nginx
sudo systemctl status nginx  # Check status
```

## Checking Nginx Version

```sh
nginx -v
```

## Nginx Configuration File

- Location: `/etc/nginx/nginx.conf` (Linux/macOS)
- Location (Windows): `C:\nginx\conf\nginx.conf`

## Testing Configuration Changes

```sh
nginx -t  # Test for syntax errors
```

## Setting Up a Simple Web Server

```sh
sudo nano /etc/nginx/sites-available/default
```

Example configuration:

```nginx
server {
    listen 80;
    server_name example.com;
    root /var/www/html;
    index index.html;
}
```

Restart Nginx after changes:

```sh
sudo systemctl restart nginx
```

## Reverse Proxy Example

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

Restart Nginx:

```sh
sudo systemctl restart nginx
```

## Blocking IPs
```nginx
server {
    listen 80;
    deny 192.168.1.1;
}
```


## Enabling SSL with Let's Encrypt

```sh
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d example.com -d www.example.com
```

## Logs and Debugging

- Access logs: `/var/log/nginx/access.log`
- Error logs: `/var/log/nginx/error.log`

```sh
tail -f /var/log/nginx/error.log
```

