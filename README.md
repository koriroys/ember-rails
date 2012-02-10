# ember-rails  [![Build Status](https://secure.travis-ci.org/keithpitt/ember-rails.png)](http://travis-ci.org/keithpitt/ember-rails)

ember-rails allows you to include [Ember.JS](http://emberjs.com/) into your Rails 3.x application.

The gem will also pre-compile your handlebars templates when building your asset pipeline. It includes development and production copies of Ember.

You can see an example of how to use the gem [here](https://github.com/keithpitt/ember-rails-example). There is also a great tutorial by [Dan Gebhardt](https://twitter.com/#!/dgeb) called "[Beginning Ember.js on Rails](http://www.cerebris.com/blog/2012/01/24/beginning-ember-js-on-rails-part-1/)" which is a great read if your just starting out with Rails and Ember.js

## Getting started

Add the gem to your application Gemfile:

    gem "ember-rails"

Run the following commands:

    bundle install
    rails g ember_rails:bootstrap

Running `rails g ember_rails:bootstrap` creates the following directory 
structure under `app/assets/javascripts/ember`:

    controllers/
    helpers/
    models/
    templates/
    views/

Additionally, it will add the following lines to `app/assets/javascripts/application.js`.
By default, it uses the Rails Application's name and creates an `rails_app_name.js.coffee` 
file to setup application namespace and initial requires.

    //= require ember
    //= require ember/app

*Example:*

    rails g ember_rails:bootstrap
      insert  app/assets/javascripts/application.js
      create  app/assets/javascripts/ember/models
      create  app/assets/javascripts/ember/models/.gitkeep
      create  app/assets/javascripts/ember/controllers
      create  app/assets/javascripts/ember/controllers/.gitkeep
      create  app/assets/javascripts/ember/views
      create  app/assets/javascripts/ember/views/.gitkeep
      create  app/assets/javascripts/ember/helpers
      create  app/assets/javascripts/ember/helpers/.gitkeep
      create  app/assets/javascripts/ember/templates
      create  app/assets/javascripts/ember/templates/.gitkeep
      create  app/assets/javascripts/ember/app.js.coffee

If you want to avoid `.gitkeep` files, use the `skip git` option like
this: `rails g ember_rails:bootstrap -g`.

Ember-rails also provides a way to run Ember in development mode, you
can switch out your require statement `//= require ember` to use the
dev copies like so:

    //= require ember-dev

Ask Rails to serve HandlebarsJS and pre-compile templates to Ember
by putting each template in a dedicated ".js.hjs" or ".handlebars" file
(e.g. `app/assets/javascripts/templates/admin_panel.handlebars`)
and including the assets in your layout:

    <%= javascript_include_tag "templates/admin_panel" %>

Bundle all templates together thanks to Sprockets,
e.g create `app/assets/javascripts/templates/all.js` with:

    //= require_tree .

Now a single line in the layout loads everything:

    <%= javascript_include_tag "templates/all" %>

## Note on Patches/Pull Requests

1. Fork the project.
2. Make your feature addition or bug fix.
3. Add tests for it. This is important so I don't break it in a future version unintentionally.
4. Commit, do not mess with rakefile, version, or history. (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
5. Send me a pull request. Bonus points for topic branches.
