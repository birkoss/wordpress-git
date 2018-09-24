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