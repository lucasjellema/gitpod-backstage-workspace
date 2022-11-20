# gitpod-backstage-workspace

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/lucasjellema/gitpod-backstage-workspace)

Based on [this tutorial Standing up Backstage](https://backstage.spotify.com/learn/standing-up-backstage/standing-up-backstage/1-intro/), the steps for creating a Backstage App are:

The installation of the Backstage instance is performed upon initialization of the Gitpod workspace. Just sit back and relax while *yarn* does its thing. It will create a directory *myapp* into which your Backstage Portal is created. When done it will run the app as well - using *yarn dev* (in a terminal) from the *myapp* directory.

The Backstage app will start both the backend and frontend app. When the terminal shows the line *[0] Webpack compiled successfully*, the Backstage app will be ready. You can then access the Backspace app at http://localhost:3000/.  

![](images/openapp.png)  

_Note_: this will work from VS Code Desktop (local terminal) - with local port forwarding. Not when running in the browser based environment: the Backstage frontend app accesses the backend API at localhost port 7007. That means that this port must both be forwarded *and* made public. 

![](images/makeportpublic.png)  

You should find your Developer Portal in good working order. Explore around - see what it has to offer in its bare, default form. 

![](images/running-app.png)  

For example:
* [the Tech Radar](http://localhost:3000/tech-radar) 
* [a sample API component](http://localhost:3000/catalog/default/api/example-grpc-api)
* [a sample Web Site component](http://localhost:3000/catalog/default/component/example-website)

Then you could start extending and fine tuning. Add some plugins, change the configuration of the portal as it currently stands.

See for example: [Configuring Plugins](https://backstage.io/docs/getting-started/configure-app-with-plugins)

### Onboarding software to Backstage

You may now want to work your way through this tutorial: [Onboarding Software to Backstage](https://backstage.spotify.com/learn/onboarding-software-to-backstage/)

## Configuring PostgreSQL as backend database

The default installation of Backstage uses SQLLite as its backend database (in memory, non-persistent acrocss workspace restarts or even Backstage restarts). The workspace already has a running PostgreSQL database and the root directory of the VS Code project contains the file *app-config.local.yaml* that has the configuration for this database as the backend. By moving this file to the *myapp* directory and restarting Backstage (*yarn dev* in the *myapp* directory) should switch Backstage from SQLLite to PostgreSQL (as explained [here](https://backstage.io/docs/getting-started/configuration)). 

Note: this does not seem to work as expected. Some more experiments seem required to get this to work properly.

To explore the PostgreSQL instance, use these commands:

```
docker exec -it backstage-postgres  psql --host=localhost  --dbname=postgres --username=postgres

\l
\c postgres
\dt
```

to connect to the database using *PSQL* in the container running the database, connecting as user *postgres* - list the database, switch to using the *postgres* database and list the currently available tables in that schema.


## Tutorials for installing and trying out Backstage

Instead of locally installing & running Backage, you can try out Backstage in the public demo environment: https://demo.backstage.io/catalog?filters%5Bkind%5D=component&filters%5Buser%5D=owned 

Introduction Backstage for All - concepts, objectives, terminology: 
https://backstage.spotify.com/learn/backstage-for-all/backstage-for-all/1-introduction/

Onboarding software to Backstage: https://backstage.spotify.com/learn/onboarding-software-to-backstage/

## Supporting Materials

Medium article - [Backstage by Example (Part 1)](https://john-tucker.medium.com/backstage-by-example-part-1-a18e74849240)

Standing up Backstage (creating your first app) - https://backstage.spotify.com/learn/standing-up-backstage/standing-up-backstage/1-intro/

[Backstage Documentation](https://backstage.io/docs/overview/what-is-backstage)

