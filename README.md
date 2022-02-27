# Active Storage DB

[![gem version](https://badge.fury.io/rb/active_storage_db.svg)](https://badge.fury.io/rb/active_storage_db)
[![linters](https://github.com/blocknotes/active_storage_db/actions/workflows/linters.yml/badge.svg)](https://github.com/blocknotes/active_storage_db/actions/workflows/linters.yml)
[![specs - Postgres](https://github.com/blocknotes/active_storage_db/actions/workflows/specs_postgres_rails7.yml/badge.svg)](https://github.com/blocknotes/active_storage_db/actions/workflows/specs_postgres_rails7.yml)
[![specs - MySQL](https://github.com/blocknotes/active_storage_db/actions/workflows/specs_mysql_rails7.yml/badge.svg)](https://github.com/blocknotes/active_storage_db/actions/workflows/specs_mysql_rails7.yml)

An Active Storage service upload/download plugin that stores files in a PostgreSQL or MySQL database.

Main features:
- supports Rails _6.0_, _6.1_ and _7.0_;
- all service methods implemented;
- attachment data stored in a binary field (or blob).

Useful also with platforms like Heroku (due to their ephemeral file system).

## Installation

- Setup Active Storage in your Rails application
- Add to your Gemfile `gem 'active_storage_db'` (and execute: `bundle`)
- Install the gem migrations: `bin/rails active_storage_db:install:migrations` (and execute: `bin/rails db:migrate`)
- Add to your `config/routes.rb`: `mount ActiveStorageDB::Engine => '/active_storage_db'`
- Change Active Storage service in *config/environments/development.rb* to: `config.active_storage.service = :db`
- Add to *config/storage.yml*:

```
db:
  service: DB
```

## Misc

Some utility tasks are available:

```sh
# list attachments ordered by blob id desc (with limit 100):
bin/rails 'asdb:list'
# search attachments by filename (or part of it)
bin/rails 'asdb:search[some_filename]'
# download attachment by blob id (retrieved with list or search tasks) - the second argument is the destination:
bin/rails 'asdb:download[123,/tmp]'
```

## Do you like it? Star it!

If you use this component just star it. A developer is more motivated to improve a project when there is some interest.

Or consider offering me a coffee, it's a small thing but it is greatly appreciated: [about me](https://www.blocknot.es/about-me).

## Contributors

- [Mattia Roccoberton](https://blocknot.es/): author
- Inspired by [activestorage-database-service](https://github.com/TitovDigital/activestorage-database-service) project

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
