The page that can be uploaded to developer.gamedistribution.com for when we want to allow a game to be self-hosted by a developer. Like with Plinga or .io games, which contain ingame payments, authentication services, etc.

Since we use postMessage to communicate we need to set correct vhosts in order to test. PostMessage API needs valid domains.

Our game source location:
``` bash
<VirtualHost *:80>
    ServerName html5.gamedistribution.com
    ServerAlias html5.gamedistribution.com
    DocumentRoot /Users/arthurhulsman/Sites/gamedistribution
    <Location />
            Options FollowSymLinks MultiViews
            Order allow,deny
            Allow from all
            Require all granted
    </Location>
</VirtualHost>

```

The partner game source location:
``` bash
<VirtualHost *:80>
    ServerName play-staging.plinga.de
    ServerAlias play-staging.plinga.de
    DocumentRoot /Users/arthurhulsman/Sites/play-staging
    <Location />
            Options FollowSymLinks MultiViews
            Order allow,deny
            Allow from all
            Require all granted
    </Location>
</VirtualHost>

```