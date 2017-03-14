# Hybris Development Boilerplate

## An [ant](http://ant.apache.org/) based Hybris development boilerplate with automations.

### Prequiresites

  - Java SDK Version >= v8
  - `ANT_HOME` defined in System environment variables (version >= 1.9.0).
  - `ANT_OPTS` defined in System environment variables (OPTIONAL), e.g. `-Xmx1024m -Dfile.encoding=UTF-8`.
  - `HYB_BIN_DIR` defined and appointed to your local Hybris `bin` package by the following orders:
    * passed in by CLI.
    * defined in System environment variables.
    * defined in `.env` (ignored by `.gitignore`).

### Features

  - all Hybris OOTB [ant](http://ant.apache.org/) tasks.
  - handy/improved version of server related tasks. 
  - `.env` based `addoninstall` and `addonuninstall` supports, pattern:

    ```bash 
    <template>.<storefront>.addonnames = <addon-a>,<addon-b>,<addon-c>
    ```

### Getting Started

  ```bash
  git clone https://github.com/jimzhan/hybris.git && cd hybris
  ant bootstrap
  ```

`bootstrap` will first try load `.env` from `${basedir}` to provide additional settings supports, then pre-defined Hybris packages will be copied into `bin` folder. Two settings profiles will be generated under `config` folder afterward:

* `config/develop` - settings profile for development (default), generated via Hybris `develop` template.
* `config/testing` - settings profile for online testing, generated via Hybris `production` template.

**NOTE** you generate new/individual settings profile using following command:

  ```bash
  ant createConfig -DHYBRIS_CONFIG_DIR=`pwd`/config/<profile> -Dinput.template=<develop|production>
  ```

### OOTB MOD

- `addoninstall` - provides `.env` based supports via specific pattern (`<template>.<storefront>.addonnames=<addon-a>,<addon-b>`)
- `addonuninstall` - provides `.env` based supports via specific pattern (`<template>.<storefront>.addonnames=<addon-a>,<addon-b>`)
- `startHybrisServer` - starts Hybris server at the foreground (default) or background (via `-Dmode=start`, synonym to tomcat arguments).
- `stopHybrisServer` - stops Hybris server at the background (if any).

### Scaffoldings 

- `bootstrap` - create a new instance with multi settings profiles supports (develop/develop, testing/production).
- `purge` - delete all generated data files and folders (`data`, `log`, `roles`, `temp` and `velocity.log`).


### Why `Ant`?

- simple, elegant and performant :heart:
- first class integration with Hybris OOTB automations.
- fast and stable, especially comparing to [Gradle](https://gradle.org/) :shit:.

**NOTE** Hybris OOTB ant tasks remain the same.


### TODOs
- [x] editor/IDE/GIT settings.
- [x] Hybris OOTB ant tasks integrations.
- [x] Multi settings profiles supports.
- [x] daemon server supports.
- [x] create new settings profile.
- [x] `addoninstall`/`addonuninstall` supports mechanism.
- [ ] checkstyle integration (pre-build).
- [ ] running server detections.
