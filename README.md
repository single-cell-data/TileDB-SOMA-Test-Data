# TileDB-SOMA-Test-Data

This project stores test and example data for TileDB-SOMA. Some examples of possible datasets that might be included are:

* an AnnData H5AD file;
* gene expression data and spatial folder from 10x's SpaceRanger (Visium processing software);
* a set of multiscale images.


## Available data

No data has been added.

## Add new raw datasets

Raw datasets and large binaries should be added to this repository as releases. A release should include the input data you need to add a desired new test or example to TileDB-SOMA.

To add new test data do the following:

1. Create a new release in the repository using the GitHub interface.
2. Pick a title for the dataset (for example "Visium v2.0.0 Dataset") and a description of what the data is. The description may include where the data was originally hosted or how it was otherwise generated.
3. Upload the desired datasets to the release by using the file dialog in the release page (at time of writing in Firefox this is done by clicking "Attach binaries by dropping them here or selecting them." in the new release page).
4. Publish the release.
5. Add a description of the new data to this README in the "Available data" section. Include the full URL to access the data (for example "https://github.com/single-cell-data/TileDB-SOMA-Test-Data/releases/download/Visium-v2.0.0-Dataset/spatial.tar.gz")


Note: Data is being added to releases instead of directly to get because we do not need the version control functionality of git for the test data and GitHub has a larger file size limit on releases than files in the repo.

## Access raw datasets

### General Access

The data can be downloaded navigating to the release or using wget or curl to access the data from the URL listed in this README.

### Add data to TileDB-SOMA

If a new dataset is needed for testing or examples in the TileDB-SOMA repository you will need to update the `scripts/prepare-test-data.sh`. Instructions on adding new data will be added to `test/README.md`.
