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

If a bot passes, it copies the manuals and the repo hashes it used to repo using a `gh` command such as

```
   gh release upload tag file -R github.com/firemodels/test_bundles --clobber
```

where file is the file that is uploaded and tag is `CFAST_TEST`, `FDS_TEST` or `SMOKEVIEW_TEST` depending on 
whether the file is a cfast, fds or smokeview manual.





<!-- comment -->
