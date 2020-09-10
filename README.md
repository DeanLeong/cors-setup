# cors-setup

![](https://media2.giphy.com/media/14j9Y06KLXsjCg/giphy.gif)

### Objectives

In this exercise, we will go over how to setup the `rack-cors` gem package with a separate rails API. All together, it can be done in three easy steps.

## Setup before the Setup

In this repo, we've included a rails app. Lets start in that directory. `cd` into the `dog_app` directory. We will need to run `bundle install`. We will also need to run `rails db:setup` to get going.

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

Let's test this out now. Create a new directory in our rails app called `client`. In the future, this will be a React app but for right now we can simulate this with just a javascript file.

1. `cd` into the `client` directory.
2. Run `npm init -y`. This will give us a `package.json` that we can add packages to (this is separate from our Rails gems).
3. touch a new file called `scratch.js`
4. run `npm install axios` in terminal.
5. At the top of our `scratch.js` file, require axios.
6. Inside of our `scratch.js` make api functions to hit each of our endpoints on the server and console.log the response.

when we're ready to test, we can call our api functions one at a time and run our `scratch.js` file with `node scratch.js` in terminal.
