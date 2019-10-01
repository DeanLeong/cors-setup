# cors-setup

### Objectives

In this exercise, we will go over how to setup the `rack-cors` gem package with a separate rails API. All together, it can be done in three easy steps.

## Setup before the Setup

In this repo, we've included a rails app. Lets start in that directory. `cd` into the `dog_app` directory. We will also need to run `rails db:setup` to get going.

## The Gem Package

In our `Gemfile`, we will find a package called 'rack-cors but it is commented out. the line will look like this:

```rb
# gem 'rack-cors'
```

We will need to uncomment that line.

## Installing Cors

Like any gem package, we will need to run `bundle install` to install any missing packages from our `Gemfile`.

In your terminal, run the command `bundle install` or `bundle` for short. these both do the same thing.

## The Config File

The last step is to fill in our config file. It can be found at `/config/initializers/cors.rb`. One thing to note is that this file only exists if we created our rails app with the `--api` flag.

Once again, we can see that Rails is being nice to us. All of the info we need is already in the comments. We will see a section that looks like this:

```rb
# Rails.application.config.middleware.insert_before 0, Rack::Cors do
#   allow do
#     origins 'example.com'
#
#     resource '*',
#       headers: :any,
#       methods: [:get, :post, :put, :patch, :delete, :options, :head]
#   end
# end
```

We can uncomment these lines. We will also need to change `example.com` to the address of our frontend client or we can tell it to except a wildcard. For now, let's give it the wild card character.

```rb
Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do
    origins '*'

    resource '*',
      headers: :any,
      methods: [:get, :post, :put, :patch, :delete, :options, :head]
  end
end
```

## Practice

Let's