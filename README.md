# powerdns-dnsui


## Generate login with htpasswd

### Requirements

````
apt install apache2-utils
````

### Generate
````
NEW_USER=admin
htpasswd -n $NEW_USER >> htpasswd
chown 33:33 htpasswd && chmod 440 htpasswd
````

### Add to htpasswd file
**Edit file and add the output from the previous command**


## Create user in DB
````
INSERT INTO public."user"
(id, uid, "name", email, auth_realm, active, "admin", developer, csrf_token)
VALUES(1, '$NEW_USER', '$NEW_USER', '$NEW_USER@example.com', 'PHP_AUTH', 1, 1, 0, NULL);
````

