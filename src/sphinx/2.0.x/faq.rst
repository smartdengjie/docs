Frequently Asked Questions
==========================

General
-------

What Eclipse Platforms are supported?
.....................................

The Scala IDE 2.0 officially supports both `Eclipse 3.6 (Helium)`__ and `Eclipse 3.7 (Indigo)`__. 

__ http://www.eclipse.org/downloads/packages/release/helios/sr2
__ http://www.eclipse.org/downloads/

What Eclipse package should I use?
..................................

The Scala IDE can be installed effortless on any of the below Eclipse packages:

* Eclipse Classic
* Eclipse IDE for Java EE Developers
* Eclipse IDE for Java Developers
* SpringSource Tool Suite

If you are using one of the above Eclipse packages you are all set and ready to :doc:`install the Scala 
IDE <gettingstarted>`.

In case you are using a different Eclipse package (e.g., Eclipse IDE for C/C++ Developers), don't panic, 
the Scala IDE has only one dependency and it's a two minutes job to update your Eclipse environment and 
be ready to start your Scala journey. 

Start by installing the Eclipse JDT (Eclipse Java Development Tools). To do so, open Eclipse and go 
to the ``Help > Install New Software`` menu, select the eclipse update site (e.g. "Indigo - 
http://download.eclipse.org/releases/indigo") and, under the Programming Languages section, select 
Eclipse Java Development Tools. Install it.

Now that the JDT is installed, go ahead and :doc:`install the Scala IDE <gettingstarted>`.

Can I install more than one Scala IDE plugin?
.............................................

Currently, it is not possible to install more than one Scala IDE plugin within the same 
Eclipse installation. You need to decide what version of Scala you want to be using and 
then choose the appropriate update site.

I have an existing Java project and I wish to add Scala files. How do I convince Eclipse to work with Scala?
............................................................................................................

Right click on the project in the Package Explorer view, and in the context menu select 
``Configure → Add Scala Nature``.

I am running out of stack space in Eclipse.  How do I increase the stack size?
..............................................................................

If you are starting Eclipse from the command line, you can supply virtual machine arguments, including stack size, like this:

.. code-block:: bash

   eclipse [normal arguments] -vmargs -Xss8M [more VM args]

You can also edit eclipse.ini in the Eclipse installation/application. There, lines that look like

.. code-block:: bash

   -vmargs
   -Xms40m
   -Xmx256m

can be replaced with something like (for an 8 megabyte stack, 700MB initial heap, 2GB maximum heap)

.. code-block:: bash

   -vmargs
   -Xss8m
   -Xms700m
   -Xmx2048m

Scala IDE complains about 'no Scala library...' or 'More than one Scala library...'
...................................................................................

In Scala IDE 2.0.0, a classpath validator has been added to check that the Scala library has been correctly setup. It is checking two points: that the project build path contains only one Scala libraries, and that its version is compatible with the installed version of Scala IDE.

Not using m2eclipse
___________________

It needs to be fixed manually.

* If the error is 'no Scala library...', one Scala library needs to be added to the build path. The simplest thing is to add the Scala library container: right-click on the project in the Package Explorer view, then in the context menu select ``Build Path → Add Libraries...``, and add the ``Scala Library``.


* If the error is 'more than one Scala library...', the number of Scala libraries needs to limited to one in the build path. If possible, make it being the Scala library container provided by Scala IDE.

Using m2eclipse
_______________

With projects imported using m2eclipse, the classpath validator can report an error because the Scala library is visible more than once in the build path. The `m2eclipse-scala`_ project was created to, among other things, fix these classpath problems.

Use this `update site`__ to get the latest version.

After installation, re-importing your projects should get them configured correctly.

__ http://alchim31.free.fr/m2e-scala/update-site/


Scala Interpreter
-----------------

What are the limitations?
.........................

* The colon commands available in the terminal REPL are not supported.
* Commands cannot be forcibly killed. For example, if an infinite loop is launched, it will continue in the background until Eclipse is shutdown.

.. include:: known-issues.rst