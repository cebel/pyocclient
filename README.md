# Python client library for ownCloud

This library makes it possible to connect to an ownCloud instance and perform
file, share and attribute operations in python.

See the [ownCloud homepage](http://owncloud.org) for more information about ownCloud.

## Features

### Accessing files

- basic file operations like getting a directory listing, file upload/download,
directory creation, etc
- read/write file contents from strings
- upload with chunking and mtime keeping
- upload whole directories
- directory download as zip

### Sharing

- share a file with public link using the OCS Share API

### App data

- store app data as key/values using the privatedata OCS API

## Usage

Example for uploading a file then sharing with link:
```python
    import owncloudclient

	oc = owncloudclient.Client('http://domain.tld/owncloud')
    oc.login('user', 'password')

	oc.mkdir('testdir')

	oc.put_file('testdir/remotefile.txt', 'localfile.txt')

	link_info = oc.share_file_with_link('testdir/remotefile.txt')

	print "Here is your link: http://domain.tld/owncloud/" + link_info.link
```

More examples can be found in the file "example.py" that actually runs a few tests
with most supported operations.
