# Heroku Migrations Buildpack

Auto-run database migrations on deployment of Rails applications in Heroku.

#### How to install on your Heroku App

```
heroku buildpacks:add https://github.com/alphasights/buildpack-migrations.git --app <my-heroku-app>
```

Once this is executed, redeploy your application.

#### How it works

This buildpack uses the `schema_migrations` table in your PostgreSQL database and compares it to the file structure in the `db/migrate` directory on your Rails app. It looks for files whose timestamps are not present as rows in `schema_migrations` and runs `bundle exec rake db:migrate` if it notices a discrepancy.
This also outputs a random Mad Max quote, because why not.

#### Contributing

Fork this repository. Then, run:

```
cd buildpack-migrations
git checkout -b my-update
git commit -m "My Update"
```

Then make a PR into this repository. 

Protip: PRs are more likely to get merged if there is at least one new quote from Mad Max added to the list.

##### Testing Your Changes

To test your changes on this buildpack using your application, follow these steps:

```
heroku buildpacks:remove https://github.com/alphasights/buildpack-migrations.git --app <my-heroku-app>
heroku buildpacks:add https://github.com/<username>/buildpack-migrations.git#my-update --app <my-heroku-app>
```

#### Copyright and License

Copyright AlphaSights and Contributors, 2015

[MIT Licence](LICENSE.txt) 