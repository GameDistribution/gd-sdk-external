The page that can be uploaded to developer.gamedistribution.com for when we want to allow a game to be self-hosted by a developer. Like with Plinga or .io games, which can contain self hosted/ maintained ingame payments, authentication services, etc.

Since we use postMessage to communicate we need to set correct vhosts in order to test. Don't forget to set some fake certificates for ssl. PostMessage API needs valid domains.

Our game source location:
``` bash
<VirtualHost *:443>
    ServerName html5.gamedistribution.com
    ServerAlias html5.gamedistribution.com
    DocumentRoot [PATH_TO_GAMEDISTRIBUTION]/html5.gamedistribution.com
    <Location />
            Options FollowSymLinks MultiViews
            Order allow,deny
            Allow from all
            Require all granted
    </Location>
    SSLEngine on
    SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
    SSLCertificateFile /etc/apache2/ssl/localhost.crt
    SSLCertificateKeyFile /etc/apache2/ssl/localhost.key
</VirtualHost>

```

The partner game source location:
``` bash
<VirtualHost *:443>
    ServerName play-staging.plinga.de
    ServerAlias play-staging.plinga.de
    DocumentRoot [PATH_TO_GAME]/play-staging.plinga.de
    <Location />
            Options FollowSymLinks MultiViews
            Order allow,deny
            Allow from all
            Require all granted
    </Location>
    SSLEngine on
    SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
    SSLCertificateFile /etc/apache2/ssl/localhost.crt
    SSLCertificateKeyFile /etc/apache2/ssl/localhost.key
</VirtualHost>

AND/ OR

<VirtualHost *:443>
    ServerName wanderers.io
    ServerAlias wanderers.io
    DocumentRoot [PATH_TO_GAME]/wanderers.io
    <Location />
            Options FollowSymLinks MultiViews
            Order allow,deny
            Allow from all
            Require all granted
    </Location>
    SSLEngine on
    SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
    SSLCertificateFile /etc/apache2/ssl/localhost.crt
    SSLCertificateKeyFile /etc/apache2/ssl/localhost.key
</VirtualHost>

```

The result is that we can host a game on a publisher portal...
``` bash
https://spele.nl

```
and have our game...
``` bash
https://html5.gamedistribution.com/714e210611d8429b982b9df68a287c07/

```
talk to our partner game.
``` bash
https://wanderers.io

```