## Readme

An application to experiment with the [Rails caching](http://guides.rubyonrails.org/caching_with_rails.html).

Demo Heroku app is [here](http://sandbox-015-caching.herokuapp.com/).

## Notes
* Uses key-based cache expiration.

    Note the use of `touch: true` to ensure that updates to child objects create a new cache key

        class Review < ActiveRecord::Base
          belongs_to :product, touch: true
        end

2. To use caching in local dev:

        config.action_controller.perform_caching = true

3. To use caching on Heroku:

        heroku addons:add memcachier

## Getting Started with this codebase

1. Install gems:

        bundle install

2. Create the database:

        rake db:create

4. Migrate the database:

        rake db:migrate

5. Start the web server:

        rails server

6. Using a browser, go to [http://localhost:3000](http://localhost:3000)

## Running the test suite

        rake

## Deploying to Heroku

1. Install the [Heroku toolbelt](https://devcenter.heroku.com/articles/getting-started-with-rails4#local-workstation-setup) on local workstation (if not already installed).

2. Create the [Heroku app](https://devcenter.heroku.com/articles/getting-started-with-rails4#deploy-your-application-to-heroku) (if not already created).

        heroku apps:create

3. [Deploy](https://devcenter.heroku.com/articles/git#deploying-code)

        git push heroku master

4. Run migrations

        heroku run rake db:migrate

5. Visit the deployed app

        heroku open

