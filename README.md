# gitpod-backstage-workspace
Gitpod workspace definition for Backstage developer portal platform 


Tutorial using an "opinionated" Docker Container Image: https://roadie.io/backstage/docker-image/

Try out Backstage in the public demo environment: https://demo.backstage.io/catalog?filters%5Bkind%5D=component&filters%5Buser%5D=owned 

## Tutorials for installing and trying out Backstage

Introduction Backstage for All
https://backstage.spotify.com/learn/backstage-for-all/backstage-for-all/1-introduction/

Standing up Backstage - https://backstage.spotify.com/learn/standing-up-backstage/standing-up-backstage/1-intro/
Onboarding software to Backstage: https://backstage.spotify.com/learn/onboarding-software-to-backstage/

## Supporting Materials

Medium article - [Backstage by Example (Part 1)](https://john-tucker.medium.com/backstage-by-example-part-1-a18e74849240)

## Get going

docker-compose up

npx @backstage/create-app

answer y to *Ok to proceed? (y)*

enter a name for the app:  `my-app`

wait for the yarn-install to complete (100-150 seconds). A new directory my-app is created. The new Backstage app is created in this directory.

cd into that directory

https://backstage.io/docs/getting-started/configuration

yarn add --cwd packages/backend pg

open app-config.yaml and add your PostgreSQL configuration. in the root directory of your Backstage app using the credentials from the previous steps.

backend:
  database:
-    client: better-sqlite3
-    connection: ':memory:'
+    # config options: https://node-postgres.com/api/client
+    client: pg
+    connection:
+      host: ${POSTGRES_HOST}
+      port: ${POSTGRES_PORT}
+      user: ${POSTGRES_USER}
+      password: ${POSTGRES_PASSWORD}


edit app-config.yml
set baseUrl (for backend apis) to refer to the endpoint exposed in gitpod on port 7007

gp url 7007

backend:
  # Used for enabling authentication, secret is shared by all backend plugins
  # See https://backstage.io/docs/tutorials/backend-to-backend-auth for
  # information on the format
  # auth:
  #   keys:
  #     - secret: ${BACKEND_SECRET}
  baseUrl: https://7007-lucasjellem-gitpodbacks-3rygnq0legf.ws-eu73.gitpod.io/
