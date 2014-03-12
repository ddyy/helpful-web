# [Helpful](http://helpful.io)
Help shouldn't hurt.

[![Build Status](https://travis-ci.org/asm-helpful/helpful-web.png?branch=master)](https://travis-ci.org/asm-helpful/helpful-web)
[![Code Climate](https://codeclimate.com/github/support-foo/web.png)](https://codeclimate.com/github/support-foo/web)
[![Inline docs](http://inch-pages.github.io/github/asm-helpful/helpful-web.png)](http://inch-pages.github.io/github/asm-helpful/helpful-web)

Helpful is an open product that's being built by a fantastic group of people on [Assembly](https://assemblymade.com/helpful). Anybody can join in building this product and earn a stake of the profit.


## Getting Started

[Vagrant](http://vagrantup.com) is the recommended way to run Helpful on your own machine. You need to download and install [Vagrant](http://vagrantup.com/downloads) before you can continue (this will take a while to run so you may want to grab some coffee).

    git clone https://github.com/asm-helpful/helpful-web.git helpful-web
    cd helpful-web
    vagrant up

Once it's finished open up [http://localhost:5000](http://localhost:5000) in your web browser to check out Helpful.


### Using Helpful

To create a new account for Helpful, click "Sign Up" on the homepage.


## Advanced Email Configuration

### Sending with Gmail

In development.rb, add:

    config.action_mailer.delivery_method = :smtp
    config.action_mailer.smtp_settings = {
        address:              'smtp.gmail.com',
        port:                 587,
        domain:               'example.com',
        user_name:            'your_gmail_username',
        password:             'your_gmail_password',
        authentication:       'plain',
        enable_starttls_auto: true
    }

### Recieving with Mailgun (optional)

Setting up [Mailgun](http://mailgun.com) in development takes a little work but allows you to use the
actual email workflow used in production.

1. Register for a free account at https://mailgun.com.
2. Get your Mailgun API key from https://mailgun.com/cp it starts with "key-"
and add it to your .env file as MAILGUN_API_KEY.
4. Get your Mailgun test subdomain from the same page and add it to your .env
file as INCOMING_EMAIL_DOMAIN.
5. In order to recieve webhooks from Mailgun we need to expose our development
instance to the outside world. We can use a tool called
[Ngrok](http://ngrok.com) for this. Download and setup Ngrok by following the
instructions on the [Ngrok](http://ngrok.com) site.
6. Run rake mailgun to make sure everything is setup right. It should prompt you
to create a route using `rake mailgun:create_route`.
7. Run `rake mailgun:create_route` and when prompted enter your Ngrok address
as the domain name.
8. Send a test email to helpful@INCOMING_EMAIL_DOMAIN and you should see it
appear in the helpful account.


## Contributing

There are a couple of steps you need to take before contributing:

1. Go to https://assemblymade.com and sign up.
2. Link your GitHub account to your Assembly account
3. Create a new WIP at https://assemblymade.com/helpful/wips. Think of WIPs as GitHub issues.

Then just go ahead, fork the repo & issue a pull request. You're on your way to having a stake in Helpful.
