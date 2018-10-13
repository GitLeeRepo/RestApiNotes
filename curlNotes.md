# Overview

Notes on the curl command line tool for transferring data via a number of protocols, including HTTP, IMAP, POP3, FILE, FTP, etc.  It is open source, it can be found on Linux distros, MacOS, and on Windows using something such as Git Bash.  Here is the 
[main website](https://curl.haxx.se/).  In some respects curl is similar to wget, but much more powerful.

# References

## My Other Notes

* [RestApiNotes](https://github.com/GitLeeRepo/RestApiNotes/blob/master/RestApiNotes.md#overview)
* [AjaxNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/AjaxNotes.md#overview)
* [JavaScriptNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/JavaScriptNotes.md#overview)
* [Angular4Notes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/Angular4Notes.md#overview)
* [JsonNotes](https://github.com/GitLeeRepo/JavaScriptNotes/blob/master/JsonNotes.md#overview)
* [NodejNotes](https://github.com/GitLeeRepo/NodejsNotes/blob/master/NodejNotes.md#overview)
* [PHPNotes](https://github.com/GitLeeRepo/PHPNotes/blob/master/PHPNotes.md#overview)
* [PythonNotes](https://github.com/GitLeeRepo/PythonNotes/blob/master/PythonNotes.md#overview)

# Command Line Options

## Test site

The curl examples here are run against the [JSONPlaceholder site](https://jsonplaceholder.typicode.com/) test site, which is a good site for testing JSON/AJAX and REST API.

* Without parameters or filters

```
curl https://jsonplaceholder.typicode.com/posts/
```
This returns all 100 of the test post JSON objects from the site

* Filter for just id:2

```
curl https://jsonplaceholder.typicode.com/posts/2
```
This returns all 100 of the post test JSON objects from the site

* Include HTTP header info along with the rest of the data

```
curl -i https://jsonplaceholder.typicode.com/posts/
```

* Include just the HTTP header

```
curl -I https://jsonplaceholder.typicode.com/posts/
```

* Download content to a specific file

```
curl -o test01.json https://jsonplaceholder.typicode.com/posts/
```
* Download a file using the server's name

```
curl -O https://jsonplaceholder.typicode.com/posts/
```
Create a file in the current directory named posts

* To upload a file to the server

```
curl -d "name=bob&title=Boss Man" https://jsonplaceholder.typicode.com/posts/
```
Note: Since this is a test server it won't actually add the data, but it gives you feedback as if it did, including assigning an id.

* To change a specific item for a specified id:

```
curl -X PUT -d "title=Test" https://jsonplaceholder.typicode.com/posts/3
```
Updates the title for id:3 to "Test"

* To delete a specific JSON object on the server based on id
```
curl -X DELETE https://jsonplaceholder.typicode.com/posts/3
```
Deletes the object associated with id:3

* To authenticate with a server

```
curl -u username:password https://thesite/thedata
```

* To upload using FTP

```
curl -u username:password -T test.txt ftp://ftp.thesite/thefolder
```

* To download using FTP

```
curl -u username:password -O ftp://ftp.thesite/thefolder/test.txt
```

## GitHub examples

Refer to:

* [GitHub API Docs](https://developer.github.com/v3/)

### GitHub Basic API

* Get specific user info

```
curl https://api.github.com/users/username
```

* Using jq (similar to awk/sed for JSON) to filter data

This returns just the value for the name key (in this case the repository names):
```
curl https://api.github.com/users/GitLeeRepo/repos | jq -r '.[].name'
```
Note this requires jq to be installed.  For Ubuntu: `sudo apt install jq`.  For Windows [download here](https://stedolan.github.io/jq/) then rename jq-win64.exe to jq.exe and place on the path.

## For GitHub operations that require authentication

* Go to [https://github.com/settings/applications/new](https://github.com/settings/applications/new) to authorize that application

* Get the Client ID and Client Secret after registering the app

* Add the credentials to your query

```
curl https://api.github.com/users/username/?client_id=xxxxxx&client_secret=xxxxxx
```

## Additional GitHub Examples

```bash
# basic information
curl -u "GitLeeRepo" https://api.github.com/users/GitLeeRepo

# gets my repos under GitLeeRepo - by default this is only the public repos
curl -u "GitLeeRepo" https://api.github.com/users/GitLeeRepo/repos

# gets all my repos both public and private including contributes on other users repos
# the page and per_page are included, otherwise it will only get the first 30 repos
curl -u "GitLeeRepo" 'https://api.github.com/user/repos?page=1&per_page=100'

# all the commits (can be very long)
curl -u "GitLeeRepo" https://api.github.com/repos/GitLeeRepo/GitInfo/commits

# with sha for the specific commit
curl -u "GitLeeRepo" https://api.github.com/repos/GitLeeRepo/GitInfo/commits/60f1026b39b33c93bc5211df80504bcc19c74579
```
