# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a
Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

- Nothing yet!

## [0.4.0] - 2022-05-15

### Added

- [esbuild-copy-static-files](https://github.com/nickjj/esbuild-copy-static-files) plugin to drastically improve how static files are copied (check `frontend/assets/esbuild.config.js`)

### Changed

- Refactor `/up/` endpoint into its own view and add `/up/databases` as a second URL

#### Languages and services

- Update `Node` to `16.14.2`
- Update `Postgres` to `14.2`
- Update `Redis` to `7.0.0`

#### Back-end dependencies

- Update `connect-redis` to `6.1.3`
- Update `ejs` to `3.1.8`
- Update `eslint-plugin-import` to `2.26.0`
- Update `eslint` to `8.15.0`
- Update `express-session` to `1.17.3`
- Update `express` to `4.18.1`
- Update `jest` to `28.1.0`
- Update `knex` to `2.0.0`
- Update `nodemon` to `2.0.16`
- Update `objection` to `3.0.1`
- Update `pg` to `8.7.3`
- Update `superagent` to `7.1.3`
- Update `supertest` to `6.2.3`

#### Front-end dependencies

- Update `autoprefixer` to `10.4.7`
- Update `esbuild` to `0.14.39`
- Update `postcss-import` to `14.1.0`
- Update `postcss` to `8.4.13`
- Update `tailwindcss` to `3.0.24`

### Fixed

- `COPY --chown=node:node ../ ../` has been fixed to be `COPY --chown=node:node . ..`

## [0.3.0] - 2021-12-26

### Added

- Lint Dockerfile with <https://github.com/hadolint/hadolint>
- `yarn:build:js` and `yarn:build:css` run script commands

### Changed

- Update `frontend/tailwind.config.js` based on the new TailwindCSS v3 defaults
- Replace all traces of Webpack with esbuild
- Move JS and CSS from `assets/app` to `assets/js` and `assets/css`
- Rename `webpack` Docker build stage to `assets`
- Copy all files into the `assets` build stage to simplify things
- Replace `cp -a` with `cp -r` in Docker entrypoint to make it easier to delete older assets
- Rename `run hadolint` to `run lint:dockerfile`
- Rename `run esbuild` to `run lint`
- Rename `run jest` to `run test`
- Rename `run bash` to `run shell`
- Rename `run frontend:yarn:outdated` to `run yarn:outdated:frontend`
- Rename `run frontend:yarn:install` to `run yarn:install:frontend`

#### Languages and services

- Update `Node` to `16.13.1` and switch to Debian Bullseye Slim
- Update `PostgreSQL` to `14.1` and switch to Debian Bullseye Slim
- Update `Redis` to `6.2.6` and switch to Debian Bullseye Slim

#### Back-end dependencies

- Update `eslint-config-airbnb-base` to `15.0.0`
- Update `eslint-plugin-import` to `2.25.3`
- Update `eslint` to `8.5.0`
- Update `express` to `4.17.2`
- Update `jest` to `27.4.5`
- Update `knex` to `0.95.15`
- Update `nodemon` to `2.0.15`
- Update `objection` to `3.0.0`
- Update `pg` to `8.7.1`
- Update `redis` to `3.1.2`
- Update `supertest` to `6.1.6`

#### Front-end dependencies

- Update `autoprefixer` to `10.4.0`
- Update `postcss` to `8.4.5`
- Update `tailwindcss` to `3.0.7`

### Fixed

- Run `yarn cache clean` after `yarn install`

### Removed

- Deleting old assets in the Docker entrypoint (it's best to handle this out of band in a cron job, etc.)

## [0.2.0] - 2021-06-18

### Added

- `bin/rename-project` script to assist with renaming the project

### Changed

- Use the Docker Compose spec in `docker-compose.yml` (removes `version:` property)
- Update PostgreSQL from `13.2` to `13.3`
- Update Redis from `6.0.10` to `6.2.4`
- Update `connect-redis` from `5.1.0` to `6.0.0`
- Update `express-ejs-layouts` from `2.5.0` to `2.5.1`
- Update `express-session` from `1.17.1` to `1.17.2`
- Update `knex` from `0.21.19` to `0.95.6`
- Update `objection` from `2.2.14` to `2.2.15`
- Update `pg` from `8.5.1` to `8.6.0`
- Update `redis` from `3.0.2` to `3.1.2`
- Update `eslint` from `7.26.0` to `7.28.0`
- Update `eslint-plugin-import` from `2.23.2` to `2.23.4`
- Update `jest` from `26.6.3` to `27.0.4`
- Update TailwindCSS to `2.2.2` and enable the JIT compiler
- Update all Webpack related dependencies to their latest versions
- Replace `APP_NAME` in `run` script with `POSTGRES_USER` for connecting to psql

### Fixed

- Fix `run` script error for unbound variable in older versions of Bash on macOS
- Remove `.js` extension in `backend/src/knex.js` import (eslint 7.26+ doesn't like it)

### Removed

- Remove Webpack's cache since the JIT compiler is pretty speedy as is

## [0.1.0] - 2021-03-11

### Added

- Everything!

[Unreleased]: https://github.com/nickjj/docker-node-example/compare/0.4.0...HEAD
[0.4.0]: https://github.com/nickjj/docker-node-example/compare/0.3.0...0.4.0
[0.3.0]: https://github.com/nickjj/docker-node-example/compare/0.2.0...0.3.0
[0.2.0]: https://github.com/nickjj/docker-node-example/compare/0.1.0...0.2.0
[0.1.0]: https://github.com/nickjj/docker-node-example/releases/tag/0.1.0
