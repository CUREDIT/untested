untested
========

Orders tests for a source code change based on code coverage analysis.

[![NPM info][nodei.co]][npm-url]

[![Build status][ci-image]][ci-status]
[![dependencies][dependencies-image]][dependencies-url]
[![endorse][endorse-image]][endorse-url]

Idea
----

Example JavaScript source organization:

	foo.js
	bar.js // uses foo.js

	tests/
		fooTest.js // tests foo.js
		barTest.js // tests bar.js

You have edited *foo.js* and rerun *tests/fooTest.js*. Are you done? No. Do you know which tests are somehow affected by *foo.js*? What if you have 100s of JavaScript source files and 100s of unit tests. Testing everything on every commit would take hours ...

**untested** is the solution.

1. Run a unit test using [*gt*](https://github.com/bahmutov/gt) or [*lasso-node*](https://github.com/bahmutov/lasso-node) or [*solid-code*](https://github.com/bahmutov/solid-code), and you get code coverage results.
2. Throw these results into **untested**.
3. On a commit give the changelist to **untested** and get back ordered list of tests affected.
4. Run these tests first. Get the results right away.

Installation
------------

You need nodejs installed, you probably need one of my other testing tools,
like [*gt*](https://github.com/bahmutov/gt) or [*lasso-node*](https://github.com/bahmutov/lasso-node).

	npm install -g untested

Usage
-----

Install *gt* (javascript testing) or *lasso-node* (html page testing with coverage) globally.

From *examples/basic* folder

	gt fooTest.js // add test point info to untested
	gt barTest.js // add test point info to untested
	untested --affected foo.js // returns both fooTest.js and barTest.js

From *examples/html* folder

	lasso-node index.html // add test point info to untested
	untested --affected foo.js // returns index.html

Integration with Git
--------------------

If you are using git, you can ask untested to run unit tests for all modified files (files returned by *git diff --name-only*).

	untested --git // returns list of unit tests for all modified files
	untested --git --run // runs unit tests for modified files using gt or lasso-node

License
-------
MIT style license, see file.

Author
------
Contact Gleb Bahmutov gleb.bahmutov@gmail.com with any questions, etc.

[nodei.co]: https://nodei.co/npm/untested.png?downloads=true
[npm-url]: https://npmjs.org/package/lasso
[dependencies-image]: https://david-dm.org/bahmutov/untested.png
[dependencies-url]: https://david-dm.org/bahmutov/untested
[endorse-image]: https://api.coderwall.com/bahmutov/endorsecount.png
[endorse-url]: https://coderwall.com/bahmutov
[ci-image]: https://secure.travis-ci.org/bahmutov/untested.png?branch=master
[ci-status]: http://travis-ci.org/#!/bahmutov/untested