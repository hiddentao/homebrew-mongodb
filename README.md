homebrew-mongodb
================

Simple setup scripts to get a mongodb replica set up and running on OSX for development work.

### Requirements
* Homebrew installed. You can find it at [http://brew.sh/](http://brew.sh/)
* mongodb installed

You can install mongodb with the following command in terminal:
``` pre
brew install mongodb
```

### Files

* homebrew.mxcl.mongodb#.plist
* mongod#.conf

### Directories Created
* /usr/local/var/log/mongodb#/
* /usr/local/var/mongodb#/

Note: *# == 1,2,3*

### Usage
Run the following commands in terminal:
``` pre
git clone https://github.com/Icehunter/homebrew-mongodb.git
cd homebrew-mongodb
./setup.sh
```
### Verification
You can verify your install by opening a mongo prompt with:
``` pre
mongo
```
It should say the following at the mongo prompt:
``` pre
rs.PRIMARY>
```

Congratulations! You now have a working local replica set with mongodb.


### Troubleshooting

If `setup.sh` is unable to connect to the running `mongod` instances then it means there was an error starting up the server. Look in the log files in `/usr/local/var/log/mongodb1` to find out the case.

If you were previously running replica sets with MongoDB 2.x and have since upgraded to 3.x then you may need to delete your existing db data folders (since they were created with the `mmapv1` engine rather than `wiredTiger` which is now the default). Your exisng db data folders are at `/usr/local/var/mongodbN` (where `N` is `1`, `2` and `3`).
