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
<li>log into the instance and set up https to secure the site</li>
<code>sudo vi https.sh</code> 
<li>make the code executable using <code>sudo chmod +x https.sh</code></li>
<li>run the bash script using <code>./https.sh</code> follow the instruction until it says success</li>
<li>you can now view the wordpress application on the browser and also see the secure certificate</li>
<li>you can then proceed to format the page by signing in as an admin</li>
<code>cat bitnami_application_password</code> this will give credentials to log in as an admin
<code> add /wp-admin</code> to the url to access the backend
