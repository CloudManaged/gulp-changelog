gulp-changelog
==============

Gulp tasks to bump the package version, create tag, commit and create change log file in one step.

It will read the `version` attribute (by default, override with `key` option) from the JSON stream (probably your `package.json` or `bower.json`), prefixes it with `"v"` (override with `prefix` option), tags the repository with such created tagname (e.g. `v1.2.3`) and create a new changelog file with the last changes.

## Prerequisites

* Git
* Python
* NodeJS

## Install

Install NodeJS dependencies:

```
npm install
```
Install Python dependencies:

```
pip install -r requirements.txt
```

## Steps

This should be how people to add new features to a project, using this `gulp task`:

1. Clone it
2. Create your feature branch (`git checkout -b new/my-new-feature`)
3. Commit your changes (`git commit -am 'new: usr: some feature'`)
4. Push to the branch (`git push origin new/my-new-feature`)
5. Create new Pull Request
6. Onces you and your team are ready to merge it:
    1. Make sure you have pulled tags down (`git fetch origin --tags`)
	2. Mark the change ([`gulp [patch|minor|major]`)
    3. Push new tag (`git push origin --tags`)
	4. Push to the branch (`git push origin new/my-new-feature`)
7. Merge into the master branch

### This is how you write your commit message:

* First line less than 50 characters very concisely message using the following conventiion:

```
ACTION: [AUDIENCE:] COMMIT_MSG [[@|!]ADJECTIVE ...]
```

> You can see a list of valid tags on the [Hashtag commit](#Hashtag commit) section.

* Use lower case when writting at least in the first line
* Second line is a blank line
* More detailed explanation in the third line
* Use the imperative when writing (fix, add instead of fixed, added)

**Example commit message**

```
new: dev: add full support to mongodm !refactor

Shanty is now deprecated in our system and we just integrate [mongodm](https://github.com/purekid/mongodm#collection)
there are a few places where shanty deprecated code have to be removed:

* Mongo_Model_User
* Mongo_Document_Contact_List

This change become important because shanty is a old, deprecated and unmaintained project
```

<a name="Hashtag commit"></a>
#### Hashtag commit

##### ACTION

* chg
* fix
* new

##### SUBJECT

* dev
* user
* pkg
* test
* doc

##### ADJECTIVE

* refactor
* minor
* cosmetic
* wip

### This is how you run the tasks:

Using `gulp` we should after we finish our new change/feature/fix inside our branch run `gulp` as following:

When we make backwards-compatible bug fixes

```
gulp patch
```

When we add functionality in a backwards-compatible manner

```
gulp minor
```

When we make incompatible API changes:

```
gulp major
```

This `gulp` commands will add a tag with the specific version according with the version in the file `package.json`

We are following the conventions used on [Semantic Versioning 2.0.0](http://semver.org/)

Dependencies
------------

* [Gulp Git](https://github.com/stevelacy/gulp-git)
* [Gulp Dump](https://github.com/stevelacy/gulp-bump)
* [Gulp Tag Version](https://github.com/ikari-pl/gulp-tag-version)

* [Python package gitchangelog](https://github.com/securactive/gitchangelog)

References
----------

* [How to contributing to a Project](http://git-scm.com/book/ch5-2.html)

* [How to writing good commit messages](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)

* [Introduction to Python package gitchangelog](https://github.com/securactive/gitchangelog/blob/master/README.rst)

TODO
----

Automate some of the task, like:

* Make sure you have pulled tags down (`git fetch origin --tags`)
* Push new tag (`git push origin --tags`)
* Push to the branch (`git push origin my-new-feature`)