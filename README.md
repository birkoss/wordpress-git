# Redirect all your uploads folder

Add this in your local **wp-content/uploads/.htaccess** to redirect all non-existing content to your *DOMAIN.COM* url.

```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule (.*) https://DOMAIN.COM/wp-content/uploads/$1
</IfModule>
```

# Force the SSL

Add this in your **.htaccess** to force all traffic in HTTPS

```
<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteCond %{HTTPS} off
	RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</IfModule>
```

# Disable the website with an .htpasswd

Add this in your **.htaccess** to force used to identify using an **.htpasswd**.

## Apache 2.4 or later

```
<IfModule mod_authn_file.c>
	AuthUserFile /FULL_PATH/.htpasswd
	AuthName "Authorization Required"
	AuthType Basic
	require valid-user
	Order allow,deny
	satisfy any
</IfModule>
```

## Apache 2.2 or lower

```
<IfModule mod_auth.c>
	AuthUserFile /FULL_PATH/.htpasswd
	AuthName "Authorization Required"
	AuthType Basic
	require valid-user
	Order allow,deny
	satisfy any
</IfModule>
```