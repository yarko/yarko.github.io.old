=====
README
======

This is a sphinx-doc version of David Richo's
copyrighted book, **The Sacred Heart of the World**.

The sources were created from a text save of
the original Word document, and then converted
to RestructuredText by hand.

This build uses a sphinx-doc 1.2 version, and
sphinx-bootstrap-theme, modified by the ``readable``
bootswatch option. Sphinx is a widely used
python documentation building system which
includes a nice, statically built search tool.
Twitter bootstrap is well known for it's
adaptable tools and components, working
well with both desktop browsers and mobile
devices.  I also use the
sphinxdoc-contrib youtube plugin.
The bootstrap based theme, along with the
modifications made, seems to work well with
the mobile devices devices tested.


Building
--------

Start on a system which has python 2.7 installed.
It is recommended to create a ``virtualenv`` and
then use the ``pip`` command to install the requirements.


.. code:: bash

   $ virtualenv Eshm   # Environment for SHM book;
   $ source Eshm/bin/activate
   $ # this is a private repository, so you will need permissions
   $ git clone https://bitbucket.org/yarko/davericho-shm
   $ cd davericho-shm
   $ pip install -r requirements.txt


You will need to install the youtube extension manually.
Using mercurial (``hg``), clone the sphinx-contrib environment somewhere convenient:


.. code:: bash

   $ hg clone https://bitbucket.org/birkenfeld/sphinx-contrib
   $ cd sphinx-contrib/youtube


At this point, the current plugin uses ``http`` protocol to connect
to youtube, but should be using ``https`` (servers would be correct
to block it otherwise).

.. code:: diff

   diff -r d9aee1952da6 -r 7e7c27a82093 youtube/sphinxcontrib/youtube.py
   --- a/youtube/sphinxcontrib/youtube.py	Wed Apr 02 00:05:18 2014 -0400
   +++ b/youtube/sphinxcontrib/youtube.py	Thu Apr 03 05:27:38 2014 -0500
   @@ -48,7 +48,7 @@
                "border": "0",
            }
            attrs = {
   -            "src": "http://www.youtube.com/embed/%s" % node["id"],
   +            "src": "https://www.youtube.com/embed/%s" % node["id"],
                "style": css(style),
            }
            self.body.append(self.starttag(node, "iframe", **attrs))
   @@ -67,7 +67,7 @@
                "border": "0",
            }
            attrs = {
   -            "src": "http://www.youtube.com/embed/%s" % node["id"],
   +            "src": "https://www.youtube.com/embed/%s" % node["id"],
                "style": css(style),
            }
            self.body.append(self.starttag(node, "iframe", **attrs))


You can fix the plugin (2 places in sphinxcontrib/youtube.py),
and then procede to install.


.. code:: bash

   $ python setup.py install


You should now be ready to build the site:

.. code:: bash

   $ make html


You can copy out the tree from ``_build/html`` where ever you are hosting this static tree.

