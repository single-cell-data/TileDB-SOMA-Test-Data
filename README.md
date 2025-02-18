# TileDB-SOMA-Test-Data

This project stores test and example data for TileDB-SOMA. Test data is stored as

## Available data

No data has been added.

## Add new raw datasets

Raw datasets and large binaries should be added to this repository as releases. This is done because we do not need the version control functionality of git for the test data and GitHub has a larger file size limit on the releases then files in the repo.

To add new test data do the following:

1. Create a new release in the repository using the GitHub interface.
2. Pick a title for the dataset (for example "Visium v2.0.0 Dataset") and a description of what the data is. The description may include where the data was originally hosted or how it was otherwise generated.
3. Upload the desired datasets to the release by using the file dialog in the release page (at time of writing in Firefox this is done by clicking "Attach binaries by dropping them here or selecting them." in the new release page).
4. Publish the release.
5. Add a description of the new data to this README in the "Available data" section. Include the full URL to access the data (for example "https://github.com/single-cell-data/TileDB-SOMA-Test-Data/releases/download/Visium-v2.0.0-Dataset/spatial.tar.gz")


* Add new test data as attachments on release.
* Update `scripts/prepare-test-data.sh` in TileDB-SOMA to download and extract new data.


## Access raw datasets

### General Access

The data can be downloaded navigating to the release or using wget or curl to access the data from the URL listed in this README.

### Add data to TileDB-SOMA

If a new dataset is needed for testing or examples in the TileDB-SOMA repository you will need to update the `scripts/prepare-test-data.sh`. Instructions on adding new data will be added to `test/README.md`.
