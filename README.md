# Redirect http to https
``` 
RewriteEngine On

RewriteCond %{HTTPS} off

RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]

```

# Redirect https to http
```
RewriteEngine On

RewriteCond %{HTTPS} on

RewriteRule (.*) http://%{HTTP_HOST}%{REQUEST_URI}

```

-------------------------------------------------------------

# Redirect www to non-www

```
RewriteCond %{HTTP_HOST} www.domain.com

RewriteRule (.*) https://domain.com/$1 [R=301,L]
```

# Redirect non-www to www
```
RewriteCond %{HTTP_HOST} ^domain.com$ [NC]

RewriteRule (.*) http://www.domain.com/$1 [R=301,L] 
```


-------------------------------------------------------------

# Adding trailing slash
```
<IfModule mod_rewrite.c>
 RewriteCond %{REQUEST_URI} /+[^\.]+$
 RewriteRule ^(.+[^/])$ %{REQUEST_URI}/ [R=301,L]
</IfModule>
```

# Removing trailing slash
```
<IfModule mod_rewrite.c>
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)/$ /$1 [L,R=301]
</IfModule>
```

-------------------------------------------------------------

# Remove .php extension from URL

```
RewriteRule ^(.+)\.php$ /$1 [R,L]
RewriteCond %{REQUEST_FILENAME}.php -f
RewriteRule ^(.*?)/?$ /$1.php [NC,END]

```

-------------------------------------------------------------

# Remove .html extension from URL

```
RewriteRule ^(.+)\.html$ /$1 [R,L]
RewriteCond %{REQUEST_FILENAME}.html -f
RewriteRule ^(.*?)/?$ /$1.html [NC,END]

```

-------------------------------------------------------------
