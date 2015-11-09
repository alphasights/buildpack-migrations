# Heroku Migrations Buildpack

Auto-run database migrations on deployment of Rails applications in Heroku.

#### How to install

```
heroku buildpacks:add https://github.com/alphasights/buildpack-migrations.git --app my-heroku-app
```

Once this is executed, redeploy your application.

#### How it works

This buildpack uses the `schema_migrations` table in your PostgreSQL database and compares it to the file structure in the `db/migrate` directory on your Rails app. It looks for files whose timestamps are not present as rows in `schema_migrations` and runs `bundle exec rake db:migrate` if it notices a discrepancy.
