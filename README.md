# CFAST, FDS and Smokeview test bundles
The [releases](https://github.com/firemodels/test_bundles/releases)
in this repo contain test bundles and manuals for the fire models
[cfast](https://github.com/firemodels/test_bundles/releases/tag/CFAST_TEST) and
[fds](https://github.com/firemodels/test_bundles/releases/tag/FDS_TEST), and the visualization program
[smokeview](https://github.com/firemodels/test_bundles/releases/tag/SMOKEVIEW_TEST).
These programs are tested daily by the scripts cfastbot, firebot and smokebot found in the 
[bot repo](https://github.com/firemodels/bot). 
If a test passes then the corresponding bundle is built
using the same repo hash as was used when running the test.
Hashes are found in the same location as bundles in the files CFAST_HASH, FDS_HASH and SMOKEVIEW_HASH.
These hashes are also found in the release title along with the date and time when the commit was made.

### Workflow

The bot and bundle scripts use the github command line tool `gh` to upload and download files to and from Github releases.
If a bot passes, it uploads manuals and repo hashes using a `gh` command such as

```
   gh release upload tag file -R github.com/firemodels/test_bundles --clobber
```

where file is the file that is uploaded and tag is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST` depending on 
whether the file is for a cfast, fds or smokeview bundle.  Repo hashes are uploaded the same way.
The `--clobber`` parameter allows uploaded files to be overwritten.

Bundle scripts download hashes and manuals from github releases using a similar `gh` command such as

```
 gh release download tag -p file -R github.com/firemodels/test_bundles -D directory --clobber
```

where file is the file downloaded, tag as before is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST` depending on 
whether the file is for a cfast, fds or smokeview bundle and directory is the directory where the file is downloaded too.

The release title is modified whenever a bundle is uplooaded to a Github release to indicate the repo hash and repo revision date.
The `gh` command used to do this is 

```
gh release edit tag -t "title of release" -R github.com/firemodels/test_bundles
```

Note, in each `gh` command firemodels could be changed to your user name (assuming you forked the test_bundles repo) to 
make changes to your forked test_bundles repo rather than the central repo version.






<!-- comment -->
