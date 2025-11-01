<h1>Wordpress deployment using aws light sail</h1>
<li>log into your aws account and search for light sail</li>
<li>click on create instance, select instance location, operating system and word press</li>
<li>select ssh key pair or create a new one</li>
<li>select pricing and give your isntance a name before launching the instance</li>
<li>select networking and attach a static ip address to the instance</li>
<li>set up a domain name at <code>duckdns.org</code></li>
<li>update the ip address to the static ip address</li>
<li>log into the instance and set up https to secure the site</li>
<code>sudo vi https.sh</code> 
<li>make the code executable using <code>sudo chmod +x https.sh</code></li>
<li>run the bash script using <code>./https.sh</code> follow the instruction until it says success</li>
<li>you can now view the wordpress application on the browser and also see the secure certificate</li>
<li>you can then proceed to format the page by signing in as an admin</li>
<code>cat bitnami_application_password</code> this will give credentials to log in as an admin
<code> add /wp-admin</code> to the url to access the backend
