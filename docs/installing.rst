************
Installation
************

On a fresh CentOS 8 or Ubuntu 18 installation, the fastest method is to use the pre-installer script:

.. code:: console

    $ ./pre-install-jrip-centos.sh
    
The above will install Webmin, Apache HTTPD Server, as well as our (optional) Certbot Module for SSL.

When the script completes, you will see the message below:

.. code:: console

    $ /opt ~
    $ Installed CertBot in /usr/share/webmin/certbot (336 kb)
    $ ~
    $ JRI Publisher is now installed. Go to Servers > JRI Publisher to complete installation


.. note::
    Following above, you will need to log in to Webmin to complete installation using the install Wizard.

Via Git or Download
===================

You can use Git to build module for an existing Webmin installation:

.. code:: console

    $ git clone https://github.com/cited/Tomcat-Webmin-Module
    $ mv Tomcat-Webmin-Module-master tomcat
    $ tar -cvzf tomcat.wbm.gz tomcat/

    
.. note::
    Following above, you will need to log in to Webmin to complete installation using the install Wizard.
