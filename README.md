# <img align="right" width="350" src="https://user-images.githubusercontent.com/1402241/83365591-7c64c200-a3a9-11ea-952e-3313c74b844f.png"> daily-version [![][badge-gzip]][link-bundlephobia]

[badge-gzip]: https://img.shields.io/bundlephobia/minzip/daily-version.svg?label=gzipped
[link-bundlephobia]: https://bundlephobia.com/result?p=daily-version

> Get the current date formatted as a version. Automatically add the time if there’s already a git tag for today’s version.

`daily-version` can be used to version your daily/nightly builds while still allowing multiple versions each day.

Based on [utc-version](https://github.com/LinusU/utc-version), uses `git` to determine whether to use the short version (e.g. `20.12.31` or the long version `20.12.31.2330` if a tag of the first version already exists)

## Install

```sh
npm install daily-version
```

## Usage

You probably want to use this via CLI, but it also has a JavaScript API.

## API

```js
const dailyVersion = require('daily-version');

dailyVersion();
// -> 17.8.29

// If 17.8.29 already exists and you call it
dailyVersion();
// -> 17.8.29.1451
// Detects the existing tag, and includes generates a sub-version based on the hours/seconds

dailyVersion('v');
// -> v17.8.29.1451
// Lets you specify any prefix
```

### dailyVersion(prefix?)

Returns a string

#### prefix

Type: `string`<br>
Optional

## CLI

```sh
$ daily-version
17.8.29

$ git tag $(daily-version)
# Creates a tag named 17.8.29

$ daily-version
17.8.29.1451
# Detects the existing tag, and includes generates a sub-version based on the hours/seconds

$ daily-version v
v17.8.29.1451
# Lets you specify any prefix
```

### \$ daily-version prefix

Outputs the version to stdout

#### prefix

Optional

### GitHub Actions

There's also an equivalent GitHub Action that makes it super easy: [daily-version-action](https://github.com/fregante/daily-version-action)
