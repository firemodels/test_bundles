# CFAST, FDS and Smokeview test bundles
The [releases](https://github.com/firemodels/test_bundles/releases)
in this repo contains test bundles and manuals for
[cfast](https://github.com/firemodels/test_bundles/releases/tag/CFAST_TEST),
[fds](https://github.com/firemodels/test_bundles/releases/tag/FDS_TEST), and
[smokeview](https://github.com/firemodels/test_bundles/releases/tag/SMOKEVIEW_TEST)/
The scripts cfastbot, firebot and smokebot found in the 
[bot repo](https://github.com/firemodels/bot) 
run daily, testing these three programs.
If the tests pass then test bundles are built
with the repo hash used by the bots when running their tests.
The hashes used to checkout the repos are found in the respective release in the files CFAST_HASH, FDS_HASH and SMOKEVIEW_HASH
and also in the release title along with the date and time when the commit was made for that hash.

<!-- comment -->
