redis-load
==========

Utility for managing data structures in Redis, allowing lists, sets, etc to be populated by loading data from flat files and JSON. Data structures can also be saved out to local files.

The rationale here was to provide an easy way to persist the results of data manipulations from Redis in common formats. Similarly, I also wanted to load data structures from files for use in Redis, but where the original data has been created separately, e.g. by a map-reduce job.

Author
______

Leigh Dodds (leigh.dodds@talis.com)

Download
--------

[http://github.com/ldodds/redis-load][0]

Installation
------------

redis-load is available as a gem:

sudo gem install redis-load

It has dependencies on the ruby redis library, json/pure and siren

If you grab a copy from github then there's an install target in the Rakefile that will build and install the gem

Usage
-----

The command-line app is called redis-load. You need to provide it with a filename and generally a key to be populated.

Load the contents of a json file as entries into a server:

    redis-load load-json --file myfile.json

Load the contents of a file as key-value pairs. (Must be key,value):

    redis-load load-keys --file mykeys.txt

Load the contents of a file into a list. Each line is a list entry:

    redis-load load-list --key mylist --file mylist.txt

Load the contents of a file into a set. Each line is a set entry:

    redis-load load-set --key myset --file myset.txt

Load the contents of a file into a sort set. Each line is a key-value pair of entry,score:

    redis-load load-zset --key myzset --file myzset.txt

Save a list into a file:

    redis-load save-list --key mylist --file mylist.txt

Save a set into a file:

    redis-load save-set --key myset --file myset.txt

Save a sorted set into a file:

    redis-load save-zset --key myzset --file myzset.txt

Note that when saving a file any existing file will automatically be over-written.

License
-------

redis-load is free and unencumbered public domain software. For more information, see http://unlicense.org/ or the accompanying UNLICENSE file.

[0]: http://github.com/ldodds/redis-load
