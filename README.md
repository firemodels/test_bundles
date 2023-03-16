# CFAST, FDS and Smokeview test bundles
The [releases](https://github.com/firemodels/test_bundles/releases)
in this repo contain test bundles and manuals for the fire models
[cfast](https://github.com/firemodels/test_bundles/releases/tag/CFAST_TEST) and
[fds](https://github.com/firemodels/test_bundles/releases/tag/FDS_TEST), and the visualization program
[smokeview](https://github.com/firemodels/test_bundles/releases/tag/SMOKEVIEW_TEST).
These programs are tested daily by the scripts cfastbot, firebot and smokebot found in the 
[bot repo](https://github.com/firemodels/bot). 
If a test passes a corresponding bundle is built
using the same version of the repo (fds, cfast and/or smv) as was used to run the test.
These bundles along with their repo hashes are uploaded to the release section of this (test_bundles) repo. 
Hashes are store in files named CFAST_HASH, FDS_HASH and SMOKEVIEW_HASH.
These hashes are also found in the release title along with the date and time when the commit was made.

### Uploading Files

Bot and bundle scripts use the github command line tool `gh` to upload and download files to and from 
a github repo release.  Bot scripts upload manuals and repo hashes (if the bot passes all its tests) 
and bundle scripts download these files to generate bundles.  
File uploads are peformed using a `gh` command such as

```
   gh release upload tag file -R github.com/firemodels/test_bundles --clobber
```

where file is the file that is uploaded and tag is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST` depending on 
whether the file is for a cfast, fds or smokeview bundle.  Repo hashes are uploaded the same way.
The `--clobber` parameter allows uploaded files to be overwritten.

### Downloading Files

File downloads are performed using a similar `gh` command

```
 gh release download tag -p file -R github.com/firemodels/test_bundles -D directory --clobber
```

where file is the file downloaded, and tag as before is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST`
depending on whether the file is for a cfast, fds or smokeview bundle and directory is the 
directory where the file is downloaded too.

### Changing a Release Title

The release title is modified whenever a bundle is uploaded to a Github repo release to indicate
the repo hash and repo revision date. The `gh` command used to do this is 

```
gh release edit tag -t "title of release" -R github.com/firemodels/test_bundles
```

### Listing and Deleting Files

To list the assests in a release using a `gh` command of the form

```
gh release view tag  -R github.com/firemodels/test_bundles
```

The `git release view` command is used to generate a list of files to be be deleted (perhaps bundles generated 
the day before).  To delete an asset or bundle use a `gh` command of the form

```
gh release delete-asset tag file -R github.com/firemodels/test_bundles -y
```

where file is the asset or bundle being deleted .  The `-y` parameter is specified to confirm that the file should be deleted.

### Note

Note, the `firemodels` parameter in each `gh` command above could be changed to your user name (assuming you forked the test_bundles repo) to 
make changes to your forked test_bundles repo rather than the central repo.






<!-- comment -->
