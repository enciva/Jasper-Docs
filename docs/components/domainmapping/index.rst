.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Domain Mapping
**********************

.. contents:: Table of Contents

Map a Domain
==============

To access the Domain Mapping manager, click the Map Domain icon as show below.

      .. image:: _static/domainmap-tab.png
      
Create Conf File
=====================


Enter a new filename.conf and click the Create button.

Give your file a name that will make it easy to identify, such as mydomain.conf
   
      .. image:: _static/domainmap-conf.png
      

Click the Create button.
      
The Create button will load the template below.

      .. image:: _static/domainmap-created.png

The template is commented.

1.  Replace all instances of DOMAIN with the domain or sub domain you wish to map.

2.  Replace '4550' to the app id and landing page (or page alias).

.. code-block:: bash
   :linenos:

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

   
Restart HTTPD
=============

For the mapping to take effect, you must restart Apache HTTPD server.

This can be done via Servers > Apache Webserver in your control panel.

It can also be done via command line using::

    service httpd restart
    
 

Edit Conf
=========

To edit a Conf File you have created, simply select the conf file from the drop down.

Make the required edits and click Save.


Conf Location
===============

By default, all conf files are saved to /etc/httpd/conf.d

      .. image:: _static/domainmap-conf-location.png
      

