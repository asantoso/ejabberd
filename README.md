Installing with mod_mam:
-   Install MongoDB  http://docs.mongodb.org/manual/
-   Install dependencies
``` bash
  $ git clone git://github.com/TonyGen/bson-erlang.git bson
  $ git clone git://github.com/DarkSideF/mongodb-erlang.git mongodb
  $ cd bson
  $ erlc -o ebin -I include src/*.erl
  $ cd ../mongodb
  $ erlc -o ebin -I include -I .. src/*.erl
  $ cd ..
  $ sudo cp -rf bson /usr/lib/erlang/lib/bson-0.1.3
  $ sudo cp -rf mongodb /usr/lib/erlang/lib/mongodb-0.3.1
```

-   Install ejabberd
``` bash
  $ git clone git://github.com/DarkSideF/ejabberd.git
  $ cd ejabberd
  $ git checkout odbc_mode -b odbc_mode
  $ ./autogen.sh
  $ ./configure --enable-odbc
  $ make
  $ sudo make install
```

-   Add config for mod_mam like:
``` yaml
odbc_type: pgsql
odbc_server: "localhost"
odbc_port: 5432
odbc_pool_size: 1
odbc_database: "ddsdabberd"
odbc_password: "dschadsas"
modules:
  mod_mam:

```
mod_mam source: `https://github.com/sdcr/ejabberd-mod-mam`

Ejabberd Community Edition, by ProcessOne
-----------------------------------------


ejabberd is a distributed, fault-tolerant technology that allows the creation
of large-scale instant messaging applications.
The server can reliably support thousands of simultaneous users on a single
node and has been designed to provide exceptional standards of fault
tolerance.
As an open source technology, based on industry-standards, ejabberd can be
used to build bespoke solutions very cost effectively.


Key Features:
=============


-   Cross-platform: ejabberd runs under Microsoft Windows and Unix derived
systems such as Linux, FreeBSD and NetBSD.
-   Distributed: You can run ejabberd on a cluster of machines and all of them
will serve the same Jabber domain(s). When you need more capacity you can
simply add a new cheap node to your cluster. Accordingly, you do not need to
buy an expensive high-end machine to support tens of thousands concurrent
users.
-   Fault-tolerant: You can deploy an ejabberd cluster so that all the
information required for a properly working service will be replicated
permanently on all nodes. This means that if one of the nodes crashes, the
others will continue working without disruption. In addition, nodes also can
be added or replaced ‘on the fly’.
-   Administrator Friendly: ejabberd is built on top of the Open Source
Erlang. As a result you do not need to install an external database, an
external web server, amongst others because everything is already included,
and ready to run out of the box. Other administrator benefits include: 
        Comprehensive documentation.
        Straightforward installers for Linux, Mac OS X.
        Web Administration.
        Shared Roster Groups.
        Command line administration tool.
        Can integrate with existing authentication mechanisms.
        Capability to send announce messages._
-   Internationalized: ejabberd leads in internationalization. Hence it is
very well suited in a globalized world. Related features are:
        Translated to 25 languages.
        Support for IDNA._
-   Open Standards: ejabberd is the first Open Source Jabber server claiming
to fully comply to the XMPP standard.
        Fully XMPP compliant.
        XML-based protocol.
        Many protocols supported._


Additional Features:
====================


Moreover, ejabberd comes with a wide range of other state-of-the-art features:

-   Modular
        Load only the modules you want.
        Extend ejabberd with your own custom modules. 
-   Security
        SASL and STARTTLS for c2s and s2s connections.
        STARTTLS and Dialback s2s connections.
        Web Admin accessible via HTTPS secure access. 
-   Databases
        Internal database for fast deployment (Mnesia).
        Native MySQL support.
        Native PostgreSQL support.
        ODBC data storage support.
        Microsoft SQL Server support. 
-   Authentication
        Internal Authentication.
        PAM, LDAP and ODBC.
        External Authentication script. 
-   Others
        Support for virtual hosting. 
        Compressing XML streams with Stream Compression (XEP-0138).
        Statistics via Statistics Gathering (XEP-0039).
        IPv6 support both for c2s and s2s connections.
        Multi-User Chat module with support for clustering and HTML logging.
        Users Directory based on users vCards.
        Publish-Subscribe component with support for Personal Eventing.
        Support for web clients: HTTP Polling and HTTP Binding (BOSH).
        IRC transport.
        Component support: interface with networks such as AIM, ICQ and MSN


Quickstart guide:
=================


0. Requirements
---------------

To compile ejabberd you need:

 - GNU Make
 - GCC
 - Libexpat 1.95 or higher
 - Libyaml 0.1.4 or higher
 - Erlang/OTP R15B or higher.
 - OpenSSL 0.9.8 or higher, for STARTTLS, SASL and SSL encryption.
 - Zlib 1.2.3 or higher, for Stream Compression support
   (XEP-0138). Optional.
 - PAM library. Optional. For Pluggable Authentication Modules (PAM).
 - GNU Iconv 1.8 or higher, for the IRC Transport
   (mod_irc). Optional. Not needed on systems with GNU Libc.
 - ImageMagick's Convert program. Optional. For CAPTCHA challenges.


1. Compile and install on *nix systems
--------------------------------------

To compile ejabberd execute the commands:

    ./configure
    make

To install ejabberd, run this command with system administrator rights
(root user):

    sudo make install

These commands will:

 - Install the configuration files in `/etc/ejabberd/`
 - Install ejabberd binary, header and runtime files in `/lib/ejabberd/`
 - Install the administration script: `/sbin/ejabberdctl`
 - Install ejabberd documentation in `/share/doc/ejabberd/`
 - Create a spool directory: `/var/lib/ejabberd/`
 - Create a directory for log files: `/var/log/ejabberd/`


2. Start ejabberd
-----------------

You can use the `ejabberdctl` command line administration script to
start and stop ejabberd. For example:

    ejabberdctl start


For detailed information please refer to the ejabberd Installation and
Operation Guide available online and in the doc directory of sources tarball.


Links:
======


 - Guide: http://www.process-one.net/docs/ejabberd/guide_en.html
 - Official site: https://www.process-one.net/en/ejabberd
 - Community site: http://www.ejabberd.im
 - Forum: http://www.process-one.net/en/forum

