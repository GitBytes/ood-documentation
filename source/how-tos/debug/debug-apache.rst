.. _debug-apache:

How to Debug Apache
===================

..  tip::

  While this page is helpful it is no replacement for `Apache Httpd's documentation`_. If
  you are an administrator responsible for Open OnDemand, you are now an administrator of
  Apache Httpd as well.  As such, you should get comfortable with it as from time to time you will
  have to troubleshoot it.


Log locations
-------------

.. _restart-apache:

Restart services
----------------

   .. tabs::

      .. tab:: RHEL/CentOS 7

        .. code-block:: sh

          sudo systemctl try-restart httpd24-httpd


      .. tab:: RHEL/Rocky 8

         .. code-block:: sh

          sudo systemctl try-restart httpd

      .. tab:: Ubuntu

         .. code-block:: sh

          sudo systemctl try-restart apache2

.. _show-virtualhosts:

Show VirtualHosts
-----------------

OpenOnDemand creates it's own `VirtualHost`_ in Apache.  Apache will route
requests based off of the hostname in the request to different VirtualHosts
and the ServerName you may have configured.

Showing virtualhosts can help debug Apache request routing.  The output from these
commands will show you how Apache is routing based off of the ServerName in the VirtualHost.

If you're seeing the default Apache webpage you likely have to :ref:`configure the ServerName <ood-portal-generator-servername>`
which corresponds directly to `Apache's ServerName configuration`_ (and restart Apache).

Or you're using the wrong hostname in your browser.

   .. tabs::

      .. tab:: RHEL/CentOS 7

        .. code-block:: sh

          sudo /opt/rh/httpd24/root/sbin/httpd -S

      .. tab:: RHEL/Rocky 8

         .. code-block:: sh

          sudo /sbin/httpd -S

      .. tab:: Ubuntu

         .. code-block:: sh

          sudo /sbin/apache2 -S


.. _Apache Httpd's documentation: https://httpd.apache.org/docs/current/getting-started.html
.. _Apache's ServerName configuration: https://httpd.apache.org/docs/2.4/mod/core.html#servername
.. _VirtualHost: https://httpd.apache.org/docs/2.4/vhosts/
