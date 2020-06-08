Username enumeration via response timing
========================================

`Lab Link <https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing>`_

Overview
########

This is all about observing response times to figure out how a web application responds differently when valid and invalid credentials are supplied. Quite often, the response times can highight when a username is valid. This excercise also demonstrates how a web server can introduce brute force protection by checking the number of attempts made by a client.

Solution
########

Determine the correct username
------------------------------

1. Make a failed login attempt to capture the request in the proxy section
2. Send the ``POST`` request to intruder with the pitchfork attack type
3. Add the ``X-Forwarded-For`` header and add it as a variable
4. Add a variable for the username
5. Set the password to be really long (over 100 chars)
6. Set the 1st payload to be a number with no decimal spaces (1-100) - spoofs the ``X-Forwarded-For`` header
7. Load the username list for the 2nd payload and run the attack
8. When finished, add the *Response received* column to the results and sort them from high to low
9. There will be one or two that have a longer, make a note of them and repeat the attack
10. One username will stand out

Determine the password
----------------------

1. Modify the position and set the username field to the value determined in the above steps
2. Add a variable for the password
3. Load the password list in the payloads
4. Set the ``X-Forwarded-For`` header a number payload
5. Run the attack

Answer
######

+----------|----------+
| Username | arcsight |
+----------|----------+
| Psssword | qazwsx   |
+----------|----------+


Key points
##########

* ``X-Forwarded-For`` can be used manipulated to trick the web application that a request has been made from a different IP address.
  * See `here <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For>`_ for details on the header and usage