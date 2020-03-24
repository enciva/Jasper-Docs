<VirtualHost *:443>
# Docs: https://xe-docs.enciva.com/en/latest/components/domainmapping/index.html
# Replace all instances of DOMAIN below with your domain or sub domain

ServerName DOMAIN

SSLEngine On

SSLCertificateFile /etc/letsencrypt/live/DOMAIN/cert.pem
SSLCertificateKeyFile /etc/letsencrypt/live/DOMAIN/privkey.pem
SSLCACertificateFile /etc/letsencrypt/live/DOMAIN/fullchain.pem

# Be sure you have generated an SSL certificate via Servers > Certbot
# Docs: https://xe-docs.enciva.com/en/latest/components/certbot/index.htmn


RewriteEngine on

# Replace 4550 below with your app id and landing page or alias

RewriteRule ^/$ ords/f?p=4550 [R=301]

ProxyRequests Off
ProxyPreserveHost On
    <Proxy *>
       Order allow,deny
       Allow from all
    </Proxy>

SSLProxyEngine On
SSLProxyCheckPeerCN off
SSLProxyCheckPeerName off
SSLProxyVerify none
ProxyPass / https://localhost:8443/ connectiontimeout=300 timeout=600
ProxyPassReverse / https://localhost:8443/

</VirtualHost>
