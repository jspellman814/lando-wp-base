## Working locally with Lando
To get started using Lando to develop locally complete these one-time steps. For further assistance please refer to the [Lando documentation](https://docs.devwithlando.io/).

* [Install Lando](https://docs.devwithlando.io/installation/installing.html), if not already installed.
* Clone this repository locally.
* Copy `lando_config/default.lando.yml` to project root and rename to `.lando.yml`.
* Run `lando start` to start Lando.
    - Save the local site URL. It should be similar to `https://<PROJECT_NAME>.lndo.site`.
* Run `lando core` to download WordPress core files.
* Run `lando set` to create a wp-config file.
* Run `lando db-import` to import a database.
* Run `lando wp search-replace "<dev_URL>" "<lando_URL>" --url=<lando_URL>`. This command replaces the staging/prod URLs with lndo.site URL.

You should now be able to edit your site locally. The steps above do not need to be completed on subsequent starts. You can stop Lando with `lando stop` and start it again with `lando start`.

Composer and wp-cli commands should be run in Lando rather than on the host machine. This is done by prefixing the desired command with `lando`. For example, run `lando wp cache flush` rather than `wp cache flush`.

There are two custom Lando commands included in default.lando.yml. In order to use, you will need to uncomment, adjust services, and point each command to the correct theme directory.
1. `lando watch` - watches and compiles theme assets.
2. `lando compile` - compiles theme assets for deploy.
