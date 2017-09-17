Whitelist on Git
=================

First Option
-------------
```bash
# First, ignore everything
*
# Now, whitelist anything that's a directory
!*/
# And all the file types you're interested in.
!*.one
!*.two
!*.etc
```

Second Option
-------------
```bash

# Blacklist files/folders in same directory as the .gitignore file
/*

# Whitelist some files
!.gitignore
!README.md

# Ignore all files named .DS_Store or ending with .log
**/.DS_Store
**.log

# Whitelist folder/a/b1/ and folder/a/b2/
# trailing "/" is optional for folders, may match file though.
# "/" is NOT optional when followed by a *
!folder/
folder/*
!folder/a/
folder/a/*
!folder/a/b1/
!folder/a/b2/
```
