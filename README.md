# ==== config untuk htaccess ===

#redirect ke SSL
RewriteEngine on
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} !^www\. [NC]
#RewriteRule (.*) link website kamu %{REQUEST_URI} [R=301,L]

# redirect the main page to landing
#RedirectMatch 302 ^/$ /landing

# remove php ext from url
# File exists but has a trailing slash
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^/?(.*)/+$ /$1 [R=301,L,QSA]

# that's we have the rules above.
RewriteCond %{REQUEST_FILENAME} !\.php
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME}\.php -f
RewriteRule ^/?(.*?)/?$ $1.php
