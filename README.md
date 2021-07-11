# opendata-higgs-discovery
 Notebooks to reproduce the Higgs discovery plots from ATLAS and CMS from public data.

## Layout of repository

You can find the notebooks to reproduce the Higgs discovery plots in the [talks](tree/main/talk) directory. The [notebooks](tree/main/notebooks) directory contains practice notebooks used to develop concepts for the analysis. They are not necessarily well documented. The talk directory contains information on what notebooks are availible.

If you were to ask - what big thing is missing? The answer would be the determination of systematic errors. The collaborations, of course, paid extensive attention to this. However, it requires a lot more data, studies, and tests, and so does note appear in these Open Data demos.

This repository was originally used for a [talk at PyHEP 2021](https://indico.cern.ch/event/1019958/contributions/4418552/).

## Using

Anyone should reproduce the ATLAS higgs plot without hesitation. Reproducing the CMS plot, however, requires real reasources: it accesses over 70 TB of data, and definately puts stresses on international infrastructure!

### ServiceX for the demo

You'll need a `servicex.yaml` file in your home directory that contains something like the following:

```
api_endpoints:
  - endpoint: http://xxx.org
    type: open_uproot
  - endpoint: http://yyy.org
    type: cms_run1_aod


backend_types:
  - type: open_uproot
    return_data: parquet
  - type: cms_run1_aod
    return_data: root
```

Please get in touch with us to get the address of the open instances running `ServiceX`.

### Setting up the environment

Setup your environment:

1. This has been run under python 3.9.6. It should work with anything that is 3.7 or greater.

1. Check out this repostiory locally, and check out the [coffea patched repository locally](https://github.com/gordonwatts/coffea).
1. For the `coffea` repository, check out the branch [pr_servicex_flat_root_files](https://github.com/gordonwatts/coffea/tree/pr_servicex_flat_root_files). For this package use the head.
1. `python -m venv .venv`, and activate the new environment.
1. `pip install -r requirements.txt`
1. In the root directory of the checked out `coffea` package, run `pip install -e[servicex]`.

From there you can start `jupyter-lab`.

If you are on windows, you'll need to make sure LongPathNames are turned on - as some of the CMS pathnames are longer than... well... heck.

### Running on binder

It is not currently possible to run on `binder` as `ServiceX` uses a non-standard port to download data.


## Plans and Status

At the talk about 45 TB of data was used for the CMS plot out of the full 70TB. Along the way, there were a number of _issues_ discovered with running with datasets that large. The [issues](/../../issues) describes a list of issues that were encountered. As they are worked on, this repository will be updated to indicate the improvements in running on the full 70 TB dataset.

## Contributions

Contributions are welcome!! Please submit as pull requests!
