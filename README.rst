GPG Key Check
=============
Check a GPG key for its expiration in a safe environment

Requirements
------------
Bash 4.2 or newer (requires `-v` availability for `if` tests)

Overview
--------

A simple program that loads a GPG key in an unique isolated environment
so that the user can examine its expiration. The environment is automatically
cleaned up.

The key is specified via the command-line parameters and may either be an
existing local file or a URL from which to download the file.

The GPG keyring is created in a temporary directory to ensure an
isolated environment.

Key File Example:

.. code-block:: bash

	$ ./gpgKeyCheck --key agentrepo.key
	Create GPG sandbox environment
	gpg: keybox '/tmp/tmp.GgaHwCZY7j/pubring.kbx' created
	gpg: /tmp/tmp.GgaHwCZY7j/trustdb.gpg: trustdb created
	Import the GPG key
	gpg: key 38077CC8F6A5034C: public key "Rackspace <support@rackspace.com>" imported
	gpg: Total number processed: 1
	gpg:               imported: 1
	Check the key
	/tmp/tmp.GgaHwCZY7j/pubring.kbx
	-------------------------------
	pub   rsa4096 2011-12-28 [SC] [expires: 2016-12-26]
	      8642D47D7D310601970F47BE38077CC8F6A5034C
		  uid           [ unknown] Rackspace <support@rackspace.com>

Download Key Example:

.. code-block:: bash

	$ ./gpgKeyCheck --url http://agentrepo.drivesrvr.com/debian/agentrepo.key
	--2016-11-29 12:46:28--  http://agentrepo.drivesrvr.com/debian/agentrepo.key
	Resolving agentrepo.drivesrvr.com (agentrepo.drivesrvr.com)... 104.130.231.18
	Connecting to agentrepo.drivesrvr.com (agentrepo.drivesrvr.com)|104.130.231.18|:80... connected.
	HTTP request sent, awaiting response... 200 OK
	Length: 1658 (1.6K) [application/octet-stream]
	Saving to: ‘/tmp/tmp.Qno4t26Tu1’

	/tmp/tmp.Qno4t26Tu1                        100%[========================================================================================>]   1.62K  --.-KB/s    in 0.005s  

	2016-11-29 12:46:28 (349 KB/s) - ‘/tmp/tmp.Qno4t26Tu1’ saved [1658/1658]

	Create GPG sandbox environment
	gpg: keybox '/tmp/tmp.QKr3a25Yrb/pubring.kbx' created
	gpg: /tmp/tmp.QKr3a25Yrb/trustdb.gpg: trustdb created
	Import the GPG key
	gpg: key 38077CC8F6A5034C: public key "Rackspace <support@rackspace.com>" imported
	gpg: Total number processed: 1
	gpg:               imported: 1
	Check the key
	/tmp/tmp.QKr3a25Yrb/pubring.kbx
	-------------------------------
	pub   rsa4096 2011-12-28 [SC] [expires: 2016-12-26]
		  8642D47D7D310601970F47BE38077CC8F6A5034C
	uid           [ unknown] Rackspace <support@rackspace.com>
