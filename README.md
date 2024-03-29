# CFAST, FDS and Smokeview test bundles

> [!WARNING]
> These bundles come with the usual disclaimer: **These bundles have passed verification testing but _not_ validation testing**.  The bundles are roughly equivalent to a maintenance release with the caveat that changes to the source worthy of a major or minor release may have been made and not yet thoroughly tested.

The [releases](https://github.com/firemodels/test_bundles/releases)
in this repo contain test bundles and manuals for the fire models
[cfast](https://github.com/firemodels/test_bundles/releases/tag/CFAST_TEST) and
[fds](https://github.com/firemodels/test_bundles/releases/tag/FDS_TEST), and the visualization program
[smokeview](https://github.com/firemodels/test_bundles/releases/tag/SMOKEVIEW_TEST).
The manuals and repo hashes/version strings are uploaded to a [github release](https://github.com/firemodels/test_bundles/releases)
whenever the corresponding bot (cfastbot, firebot and smokebot) found in the 
[bot repo](https://github.com/firemodels/bot) completes without error. The bundles are then built
and uploaded to the same release by separate bundle scripts.
These scripts use the uploaded repo hashes and version strings to build the bundles.
Hashes and repo version strings are stored in files named CFAST_INFO.txt, FDS_INFO.txt and SMOKEVIEW_INFO.txt.
These strings are also found in the release title along with the date and time when the commit was made.

### Uploading Files

Bot and bundle scripts use the github command line tool `gh` to upload and download files to and from 
a github repo release.  Bot scripts upload manuals and repo hashes (if the bot passes all its tests) 
and bundle scripts download these files to generate bundles. Files are uploaded using a `gh` command such as

```
   gh release upload tag file -R github.com/firemodels/test_bundles --clobber
```

where file is the file that is uploaded and tag is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST` depending on 
whether the file is for a cfast, fds or smokeview bundle.  Repo hashes are uploaded the same way.
The `--clobber` parameter allows uploaded files to be overwritten.

### Downloading Files

File downloads are performed using a similar `gh` command


```
 gh release download tag -p file -R github.com/firemodels/test_bundles -D outdir --clobber
```

where file is the file downloaded, and tag as before is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST`
depending on whether the file is for a cfast, fds or smokeview bundle.  `outdir` is the 
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

### Notes

*   The first time `gh` is used you will be asked to authenticate by typing
`gh auth login`.  This command will output a code and ask you to login to your github account to 
enter that code.  `gh` may then be used to access your github repos.

*  The bot and bundle scripts in this repo using `gh` use several bash environment variables to access your github repos so that changes can be made
if necessary without changing scripts (for example to access your forked test_bundles repo when testing scripts instead of the central
repo version).

```
GH_OWNER=firemodels
GH_REPO=test_bundles
GH_CFAST_TAG=CFAST_TEST
GH_FDS_TAG=FDS_TEST
GH_SMOKEVIEW_TAG=SMOKEVIEW_TEST
```

*   The `firemodels` parameter in each `gh` command above could be changed to your user name (assuming you forked the test_bundles repo) to 
make changes to your forked test_bundles repo rather than the central repo.







<!-- comment -->
