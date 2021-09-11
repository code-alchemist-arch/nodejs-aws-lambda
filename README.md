# Serverless Node.js Project

[![npm](https://img.shields.io/npm/v/@makenew/nodejs-aws-lambda.svg)](https://www.npmjs.com/package/@makenew/nodejs-aws-lambda)
[![GitHub Actions](https://github.com/makenew/nodejs-aws-lambda/workflows/main/badge.svg)](https://github.com/makenew/nodejs-aws-lambda/actions)

Package skeleton for a Node.js Serverless project on AWS Lambda.

## Description

Bootstrap a new Node.js Serverless project in five minutes or less.

### Features

- Deploy to [AWS Lambda] under a
  [custom domain][serverless-domain-manager] with [Serverless].
- [Node.js]'s [npm] package structure.
- Fast, reliable, and secure dependency management with [Yarn].
- Examples with configurable options and arguments powered by [examplr].
- Linting with the [JavaScript Standard Style] using [ESLint].
- [Prettier] code.
- Futuristic debuggable unit testing with [AVA].
- Code coverage reporting with [Istanbul] and [nyc].
- Continuous deployment, testing, and package publishing with [GitHub Actions].
- [Keep a CHANGELOG].
- Consistent coding with [EditorConfig].
- Badges from [Shields.io].

[AVA]: https://github.com/avajs/ava
[AWS Lambda]: https://aws.amazon.com/lambda/
[ESLint]: https://eslint.org/
[EditorConfig]: https://editorconfig.org/
[GitHub Actions]: https://github.com/features/actions
[Istanbul]: https://istanbul.js.org/
[JavaScript Standard Style]: https://standardjs.com/
[Keep a CHANGELOG]: https://keepachangelog.com/
[Node.js]: https://nodejs.org/
[Prettier]: https://prettier.io/
[Serverless]: https://serverless.com/
[Shields.io]: https://shields.io/
[Yarn]: https://yarnpkg.com/
[examplr]: https://github.com/meltwater/node-examplr
[npm]: https://www.npmjs.com/
[nyc]: https://github.com/istanbuljs/nyc
[serverless-domain-manager]: https://github.com/amplify-education/serverless-domain-manager

### Bootstrapping a new project

1. Create an empty (**non-initialized**) repository on GitHub.
2. Clone the master branch of this repository with
   ```
   $ git clone --single-branch git@github.com:makenew/nodejs-aws-lambda.git <new-node-lib>
   $ cd <new-node-lib>
   ```
   Optionally, reset to the latest version with
   ```
   $ git reset --hard <version-tag>
   ```
3. Run
   ```
   $ ./makenew.sh
   ```
   This will replace the boilerplate, delete itself,
   remove the git remote, remove upstream tags,
   and stage changes for commit.
4. Create the required GitHub repository secrets.
5. Review, commit, and push the changes to GitHub with
   ```
   $ git diff --cached
   $ git commit -m "Replace makenew boilerplate"
   $ git remote add origin git@github.com:<user>/<new-node-lib>.git
   $ git push -u origin master
   ```
6. Ensure the GitHub action passes,
   then publish the initial version of the package with
   ```
   $ nvm install
   $ yarn install
   $ npm version patch
   ```
7. Ensure a valid certificate exists in [AWS Certificate Manager]
   that matches the custom deployment domains,
   e.g., this project uses a wildcard certificate for
   `*.nodejs-aws-lambda.makenew.razorx.app`.
   Then trigger a deploy to the stg stage with
   ```
   $ yarn run release:staging
   ```

[AWS Certificate Manager]: https://aws.amazon.com/certificate-manager/

### Updating from this skeleton

If you want to pull in future updates from this skeleton,
you can fetch and merge in changes from this repository.

Add this as a new remote with

```
$ git remote add upstream git@github.com:makenew/nodejs-aws-lambda.git
```

You can then fetch and merge changes with

```
$ git fetch --no-tags upstream
$ git merge upstream/master
```

#### Changelog for this skeleton

Note that `CHANGELOG.md` is just a template for this skeleton.
The actual changes for this project are documented in the commit history
and summarized under [Releases].

[Releases]: https://github.com/makenew/nodejs-aws-lambda/releases

## Installation

Add this as a dependency to your project using [npm] with

```
$ npm install @makenew/nodejs-aws-lambda
```

or using [Yarn] with

```
$ yarn add @makenew/nodejs-aws-lambda
```

[npm]: https://www.npmjs.com/
[Yarn]: https://yarnpkg.com/

## Development and Testing

### Quickstart

```
$ git clone https://github.com/makenew/nodejs-aws-lambda.git
$ cd nodejs-aws-lambda
$ nvm install
$ yarn install
```

Run the command below in a separate terminal window:

```
$ yarn run test:watch
```

Primary development tasks are defined under `scripts` in `package.json`
and available via `yarn run`.
View them with

```
$ yarn run
```

### Source code

The [source code] is hosted on GitHub.
Clone the project with

```
$ git clone git@github.com:makenew/nodejs-aws-lambda.git
```

[source code]: https://github.com/makenew/nodejs-aws-lambda

### Requirements

You will need [Node.js] with [npm], [Yarn], and a [Node.js debugging] client.

Be sure that all commands run under the correct Node version, e.g.,
if using [nvm], install the correct version with

```
$ nvm install
```

Set the active version for each shell session with

```
$ nvm use
```

Install the development dependencies with

```
$ yarn install
```

[Node.js]: https://nodejs.org/
[Node.js debugging]: https://nodejs.org/en/docs/guides/debugging-getting-started/
[npm]: https://www.npmjs.com/
[nvm]: https://github.com/creationix/nvm

### Publishing

Use the [`npm version`][npm-version] command to release a new version.
This will push a new git tag which will trigger a GitHub action.

Publishing may be triggered using on the web
using a [version workflow_dispatch on GitHub Actions].

[npm-version]: https://docs.npmjs.com/cli/version
[version workflow_dispatch on GitHub Actions]: https://github.com/makenew/nodejs-aws-lambda/actions?query=workflow%3Aversion

### Deployment

Serverless deployment is triggered by a release repository_dispatch on GitHub Actions.

Ensure a `GITHUB_TOKEN` is set in your environment and
use `yarn run release:<environment>` to do this automatically, e.g.,

```
$ yarn run release:staging
$ yarn run release:production
```

Deployment may be triggered using on the web
using a [release workflow_dispatch on GitHub Actions].

[npm-version]: https://docs.npmjs.com/cli/version
[release workflow_dispatch on GitHub Actions]: https://github.com/makenew/nodejs-aws-lambda/actions?query=workflow%3Arelease

## GitHub Actions

_GitHub Actions should already be configured: this section is for reference only._

The following repository secrets must be set on [GitHub Actions]:

- `NPM_TOKEN`: npm token for installing and publishing packages.
- `AWS_DEFAULT_REGION`: The AWS region Serverless will deploy to.
- `AWS_ACCESS_KEY_ID`: AWS access key ID.
- `AWS_SECRET_ACCESS_KEY`: AWS secret access key.
- `GH_TOKEN`: A personal access token that can trigger workflows.

These must be set manually.

### Secrets for Optional GitHub Actions

The version and format GitHub actions
require a user with write access to the repository.
including access to trigger workflows.
Set these additional secrets to enable the action:

- `GH_USER`: The GitHub user's username.
- `GH_TOKEN`: A personal access token for the user.
- `GIT_USER_NAME`: The GitHub user's real name.
- `GIT_USER_EMAIL`: The GitHub user's email.
- `GPG_PRIVATE_KEY`: The GitHub user's [GPG private key].
- `GPG_PASSPHRASE`: The GitHub user's GPG passphrase.

[GitHub Actions]: https://github.com/features/actions
[GPG private key]: https://github.com/marketplace/actions/import-gpg#prerequisites