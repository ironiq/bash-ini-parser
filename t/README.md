# Test suite

This test suite is based on [sharness](http://felipec.github.io/sharness/)

# Install

It is installed (from toplevel dir) with:

    git submodule add --branch master https://github.com/felipec/sharness t/sharness

and update from time to time with:

    git submodule update --force t/sharness

Read http://blogs.atlassian.com/2013/05/alternatives-to-git-submodule-git-subtree/ for more info on git subtree, you can define a remote to simplify commands or contribute sharness from your fork

# Automation

Although every test is executable by itself an only depends on sharness, that's not operative. this test suite relays on [prove](http://search.cpan.org/dist/Test-Harness/bin/prove) and ancient and good-know [make](http://www.gnu.org/software/make/) to complete the test suite. Launch it with 

    make

or

    make DEFAULT_TEST_TARGET=prove

for tap output

    make DEFAULT_TEST_TARGET=tap SHELL=/bin/bash

# Credits

Makefile was shamelessly stolen from [git-integration](https://github.com/johnkeeping/git-integration/blob/master/t/Makefile)

Test cases are strongly based on [bash_ini_parser test suite](https://github.com/rudimeier/bash_ini_parser/blob/master/test/test.sh)


