<h1>Wordpress deployment using aws light sail</h1>
<h3>log into your aws account and search for light sail</h3>
<li>click on create instance
<li>select instance location</li>
<li>select operating system
<li>select word press</li>
<h3>creating a key pair</h3>
<li>create a new keypair or select an existing one</li>
<h3>aws light sail pricing</h3>
<li>select pricing, I use the lowest price of 5$</li>
<li>name your instance before launching it</li>
<h3>networking</h3>
<li>select networking and attach a static ip address to the instance</li>
<h3>setting up domain name</h3>
<li>set up a domain name at <code>duckdns.org</code> and check for its availability</li>
<li>change the defaukt ip address genrated by <code>duckdns.org</code> to the static ip address you created in aws</li>
<h3>logging in to the instance using mobaxterm</h3>
<li>on the mobaxterm terminal, add the username, static ip address and keypair to connect to the instance created
<h3>creating ssl certificate</h3>
<li>on the instance<code>sudo vi https.sh</code></li>
<li>copy the code into the <code>https.sh</code>
<code>
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

</code>
<li>make the code executable using <code>sudo chmod +x https.sh</code></li>
<h3>run the bash script</h3>
<li>use <code>./https.sh</code> to run the script, follow the instruction until it says successful</li>
<h3>word press deployment</h3>
<li>you can now view the secured wordpress application on the browser by passing in the domain name</li>
<h3>accessing the backend of the wordpress application</h3>
<li>to accesss the admin credentials use<code>cat bitnami_application_password</code>
<li><code>@domainname.com/wp-admin</code>
<li>you can now proceed to log in using the credentials and url above</li>
