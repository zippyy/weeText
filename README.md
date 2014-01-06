weeText
=======

Text messaging script for Weechat using Google Voice

### Usage:

1) Edit the script or ```~/.weechat/plugins.conf``` and input
your credentials.

plugins.conf:

     python.weetext.email = "your_address@gmail.com"
     python.weetext.passwd = "${sec.data.weetext}"
     python.weetext.poll_interval = "2"

or, if you don't want to use the /secure password storage
in weechat:

     python.weetext.passwd = "mypasswd"

Load the script and weechat should connect to Google Voice.
Then after "polling_interval" seconds, you should see
all of your available text message conversations - one
buffer per phone number.

In the weetext window, you can open text message windows
to additional phone numbers by typing the command:

     text 0123456789

This will open a texting window to phone number 0123456789.

Finally, weeText incorporates the possibility of symmetric encryption
of text messages using OpenSSL. The code for this comes directly from
the crypt.py script, and you are encouraged to take a look at that
script for usage instructions. One small difference, the cryptkey.*
files are stored in ```%h/cryptkey``` rather than in ```%h``` as is
the case for the crypt.py script

### Todos:

1. non-blocking ```recText()``` and ```login()```
The login() at script load time takes about 20 seconds. But that only
needs to be done once. Receive text polling takes just a couple of
seconds, but it should be possible to eliminate that as well.

Enjoy!
