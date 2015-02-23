# Staytus

Staytus is a complete solution for publishing the latest information about
any issues with your web applications, networks or services. Along with
absolutely beautiful public & admin interfaces, Staytus is a powerful tool for
any organization with customers rely on them to be online 24/7.

![Screenshot](https://s.adamcooke.io/15/vGMNR1.png)

## System Requirements

* Ruby 2.1 or greater
* RubyGems and Bundler
* A MySQL database server

## Installation from source

Currently the only way to install Stayus is from the source repository.
To do this, you'll need Git installed.

Before start, you'll need to create a new MySQL database:

```text
mysql$ CREATE DATABASE `staytus` CHARSET utf8 COLLATE utf8_unicode_ci;
mysql$ GRANT ALL ON staytus.* TO `staytus`@`localhost` IDENTIFIED BY "a_secure_password";
```

```text
$ git clone https://github.com/adamcooke/staytus
$ git checkout stable
$ cd staytus
$ bundle install --deployment --without deployment:test
$ cp config/database.example.yml config/database.yml
$ nano -w config/database.yml # Add your database configuration
$ bundle exec rake staytus:build staytus:install
$ bundle exec rails server
```

This will run the application on HTTP port 8787. When you first
login, you'll be able to add your own site settings. Browse to http://[IP]:8787
to begin.

### Upgrading

Once you've installed Staytus, you can easily upgrade it by
following this process.

```text
$ cd path/to/staytus
$ git pull origin stable
$ bundle
$ bundle exec rake staytus:build staytus:upgrade
```

Once you've done this, you should ensure you restart any Staytus
processes which you have running.

## Themes

All themes are stored in the `content/themes` directory. You can
add your own these in this directory but we do not recommend
making changes to the `default` theme as these changes may get
overriden in an upgrade.

Full details about how to make these will be coming soon.
