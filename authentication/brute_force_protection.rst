Broken brute-force protection, IP block
=======================================

`Lab link <https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block>`_

Overview
########

This lab demonstrates how to get around the brute force defense of stopping login attempts after a failed number of attempts.

Solution
########

1. Make a request for the login and send the payload to intruder using the pitchfork attack
2. Set variables for username and password
3. We know the correct username is carlos, so we need to create a `list of usernames <./usernames.txt>`_ that alternate between *peter* and *carlos*.
4. Create a second file with the password *peter* alternating between the ones int he file ``awk '{print "peter\n"$0}' passwords.txt > password_mod.txt``. Use `this file <./password_mod.txt>`_.
5. Run the attack
6. When finished, look for a *302* response for carlos.

Answer
######

+----------+----------+
| Username | carlos   |
+----------+----------+
| Password | ashley   |
+----------+----------+

Key points
##########

* To get around the brute force protection, you need to have a set of valid creds that you know work and use these to create a password list.