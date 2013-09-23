# shouter

An example application that uses a JDBC connection to a postgresql database and the composure web framework.

## Usage

To run locally start a postgresql database:

    sudo su postgres -c '/opt/local/lib/postgresql92/bin/postgres -D /opt/local/var/db/postgresql91/defaultdb'

To create the 'shouts' table in the database run the migration script:

    lein run -m shouter.models.migration

To run the shouter server locally use:

    foreman start

To deploy to Heroku:

    heroku create
    heroku addons:add heroku-postgresql:dev // provisions remote database

Push the code to Heroku.

    git push heroku master

Then run the database migration script against the newly provisioned database.

    heroku run lein run -m shouter.models.migration

With the database provisioned, scale web dynos up:

    heroku ps:scale web=1

Check app is running:

    heroku ps

Finally open the live application in browser:

    heroku open

To restart the postgres database server locally:

    sudo su postgres -c 'pg_ctl -D /opt/local/var/db/postgresql84/defaultdb/ restart'

To stop the postgres server locally:

    sudo su postgres -c 'pg_ctl -D /opt/local/var/db/postgresql84/defaultdb/ stop'


## License

Copyright © 2013 FIXME

Distributed under the Eclipse Public License, the same as Clojure.
