apache-visualsvn-server
=======================

Use current project as example for setting-up a directory structure of Apache server configured as VisualSVN server on Ubuntu 12.04

Subversion repositories are available under HTTPS protocol at https://localhost:8443/svn/


Repositories
------------

  svnadmin create /var/svn/repos/REPO_NAME
  chown -R www-data:www-data /var/svn/repos/REPO_NAME

All repositories will be accessible via https://localhost:8443/svn/


Access
------

<pre><code>
Username: demo
Password: demo
</code></pre>

To add new user:

<pre><code>
htpasswd -m /var/svn/dav_svn.htpasswd <ENTER_USER_NAME_HERE>
</code></pre>

Setting permissions per project: see file /var/svn/dav_svn.authz


ACL permissions
---------------

All Subversion directories must be writable by Apache (www-data).

<pre><code>
chown -R www-data:www-data /var/svn/
chown -R www-data:www-data /var/www/
</code></pre>

SSL certificate
---------------

You can either use CA (certification authority) or self-signed certificate. Put it in file /etc/apache2/ssl.key/server.pem

Read about creation and self-signing on https://devcenter.heroku.com/articles/ssl-certificate-self for example.


Checkout
--------

You can now checkout the revision zero of your subversion repository by:

<pre><code>
svn checkout https://localhost:8443/svn/REPO_NAME
</code></pre>
