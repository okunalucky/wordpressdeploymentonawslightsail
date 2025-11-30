# WORDPRESS DEPLOYMENT USING AWS LIGHT SAIL
<img width="841" height="581" alt="Image" src="https://github.com/user-attachments/assets/080e10f6-3106-40bb-976b-f8f8de8b9ca7" />



- Log into your aws account and search for light sail
- Click on create instance: select instance location, operating system, wordpress
- Create a key pair: create a key pair or select an existing one
- Seclect aws light sail pricing: use the lowest price of 5$
- Name your instance before launching it
- Networking: select networking and attach a static ip address to the instance
- Set up domain name: check for its availability at duckdns.org
- Change the default ip address to the static ip address you created in aws
- Log  in to the instance using mobaxterm: we need username, static ip address and key pair to connect to the instance created
- Create the ssl certificate using: 
```sh
  vi https.sh
```
- Paste the code into https.sh
  
```sh
  #!/usr/bin/env bash
# Helper: Launch Bitnami's HTTPS configuration tool for Let's Encrypt
# Note: bncert-tool is interactive; ensure your DuckDNS domain resolves to this instance IP.
set -euo pipefail

if [[ ! -x "/opt/bitnami/bncert-tool" ]]; then
  echo "Bitnami bncert-tool not found at /opt/bitnami/bncert-tool" >&2
  exit 1
fi

echo "Opening Bitnami HTTPS configuration tool..."
echo "Prereqs:"
echo " 1) DuckDNS subdomain points to this instance's STATIC IP"
echo " 2) Ports 80 and 443 open in Lightsail Networking"
echo " 3) Be ready to enter your domain (e.g., mysite.duckdns.org)"
sudo /opt/bitnami/bncert-tool
```
- Make the code executable using:
```sh
  sudo chmod +x https.sh
```
- Run the bash script
```sh
./https.sh
```
- Follow the instruction until it says successful
-  You can now view the secured wordpress application on the browser by passing in the domain name

# THE STATIC WEBSITE
<img width="967" height="603" alt="Image" src="https://github.com/user-attachments/assets/5708a3e6-4187-45e0-9f50-039bcc722b6d" />

- Access the backend of the wordpress application
```sh
cat bitnami_application_password
```
```sh
  @domainname.com/wp-admin
  ```
- You can now proceed to log in using the credentials and url above
- Formatting the wordpress application
- After logging in to the backend using the credentials, you can select any theme of your choice under appearance and save changes, it will be effected instantly

# FORMATTED WEBSITE
<img width="1245" height="658" alt="Image" src="https://github.com/user-attachments/assets/fee2333f-1d50-45c0-aab1-2b32d55180e5" />

