# Suse Manager - Quick Start Guide


Really Quick
============

Download the iso from: https://www.suse.com/products/suse-manager/download/#

Install it, set up your hostname, run:
```
yast2 susmanager_setup
```

Set up channel connections with:

```
mgr-ncc-sync -c $CHANNEL_NAME
```

Log in to the Suse Manager web interface, create some keys, and then run the bootstrap manager:

```
mgr-bootstrap
```

Then, on the client machine:

```
wget https://suse-manager.FQ.DN/pub/bootsrap/bootstrap.sh
sh ./bootstrap.sh
```


Done!

A bit more detail
=================

In order to download the iso, you'll need to sign up for a trial, entering appropriate items into the form at https://www.suse.com/products/suse-manager/download/#

Next, you'll need to install the iso on a machine, virtual or othwerwise, accepting defaults, changing as necessary.

Once installed, you'll need to set up your hostname so that the command

```
hostname -f
```

works.  This can be done through yast by goign to Network Devices -> Network Settings -> Hostname/DNS.  A reboot will be needed.


Next, run:

```
yast2 susemanager_setup
```

You'll need to provide it the relevant details for an SSL Certificate Authority, and the location and credentials for your database servers if you're not going to have them local. Next add your Novell mirror credentials, and then the setup will get things squared away!

Once that's finished, you'll set up your repository sync's with:

```
mgr-ncc-sync -l
```

which lists the available channels, to import channels

```
mgr-ncc-sync -c $CHANNEL_NAME
```


Next, we'll configure a bootstrap script, which you can run on machines you wish to connect to Suse Manager:

```
mgr-bootstrap
```

And finally, on any client machine:

```
wget http://<suse-manager-hostname>/pub/bootstrap/bootstrap.sh
./bootstrap.sh
```

This document Copyright 2015 Paul Warren <pwarren@pwarren.id.au> and released under CC-By-SA
