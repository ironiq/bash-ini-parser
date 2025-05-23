# bash-ini-parser

A ini file parser for bash relying only on builtins

# Usage

You must copy [bash-ini-parser](https://github.com/ironiq/bash-ini-parser/blob/main/bash-ini-parser) on your project and source it:

    $ source bash-ini-parser

or

    $ . bash-ini-parser

Then, there is a properties file (file.ini):

    [section]
       key = value
       key2 = value2

Issuing:

    $ cfg_parser file.ini

Will declare functions per ini section called *cfg&#95;section&#95;&lt;section&gt;* which declares variables named as keynames so you can access its values using

    $ cfg_section_<section>
    $ echo $key
    value
    $ echo $key2
    value2

# Updating and saving changes

To update a value

    var=new_value
    cfg_update <sec> <var>

To save changes

    cfg_writer > newfile.ini

> Take care that saving function will loose comments and indentation, use with care

# Example

Goto scripts directory and launch [example.sh](https://github.com/ironiq/bash-ini-parser/blob/main/scripts/example.sh)

    $ cd scripts
    $ ./example.sh

Inspect its code, reuse on your scripts

# Checking an ini file

If you want to test your existing ini file use [getkeyfromsection.sh](https://github.com/ironiq/bash-ini-parser/blob/main/scripts/getkeyfromsection.sh)

    $ getkeyfromsection.sh <file.ini> sectionname keyname

e.g.:

See [file.ini](https://github.com/ironiq/bash-ini-parser/blob/main/scripts/file.ini), it is a file with different indentations, and comments

Issuing:

    $ ./testfile.sh file.ini sec1 var4

Outputs:

    show parsed file.ini
    [sec1]
    var1="foo"
    var2="hoge"
    var3="fuga"
    var4="pivo"
    [sec2]
    var1="bar"
    var2="foo"
    var3="eco"
    var4="piyo baz qux"
    var5="foo"
    var6="hoge"

    var4 value is "pivo"

# Debugging

declare **BASH_INI_PARSER_DEBUG** and parse will output the ini file processing

# Hacking zone

bash-ini-parser is based on bash env vars, which do not support all valid characters for ini files. You can define a function to replace dangling characters, See [t0009-invalid-chars.sh](https://github.com/ironiq/bash-ini-parser/blob/main/t/t0009-invalid-chars.sh)

# Drawbacks

This is more a hack than a reliable parser, so keep in mind things like

 - multiword value vars will be arrays so you must access it as `${var[*]}`

For a trusted parser (but based on python) checkout [crudini](https://github.com/pixelb/crudini)

# Alternatives

[bash_ini_parser](https://github.com/albfan/bash_ini_parser) - The origin of this repo.

[bash_ini_parser](https://github.com/rudimeier/bash_ini_parser) - A slightly different approach.

