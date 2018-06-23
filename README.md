# Block country with Nginx
Block country using the Nginx deny rule without any additional module needed


## Installation
1. Instal the unzip software 
```
sudo apt-get install unzip 
```

2. Install the Nginx
```
sudo apt install nginx
```

3. Create the directory to store the block country list
```
sudo mkdir /etc/nginx/country-cidr && cd /etc/nginx/country-cidr
```

4. Download the country list from gypthecat.com
```
sudo wget http://firewalliplists.gypthecat.com/lists/nginx/nginx-countries.conf.zip
```

5. Unzip the country list
```
sudo unzip nginx-countries.conf.zip
```

6. Edit the nginx.conf
```
server
{
	listen 80;
	server_name www.companya.com companya.com;
	root /webhost/companya.com/httpdocs/;
	access_log /webhost/companya.com/logs/access.log combined;
	error_log /webhost/tld.co.uk/logs/error.log;
	index index.php index.html index.htm;

	location / {
		allow 175.13.5.10;
		include country-cidr/MY-deny.conf;
		allow all;
		# Do something here
    }

}
```

7. Restart the nginx
```
sudo service nginx restart
```




