# TileDB-SOMA-Test-Data

This project stores test and example data for the [TileDB-SOMA repository](https://github.com/single-cell-data/TileDB-SOMA). Some examples of possible datasets that might be included are:

* an AnnData H5AD file;
* gene expression data and spatial folder from 10x's SpaceRanger (Visium processing software);
* a set of multiscale images stored as a tar file.


## Available data

* 2025-02-19: No data has been added to date.

## How to add new datasets

This repository exists to store large binaries and similar artifacts needed as test or example inputs for TileDB-SOMA. The data will be added to this repository as a release.

To add new test data do the following:

1. Create a new release in the repository using the GitHub interface.
2. Set the title using the format "Dataset YYYY-MM-DD" (for example "Dataset 2025-02-19").
3. Set the tag to "dataset-YYYY-MM-DD" (for example "dataset-2025-02-19").
4. Add a description of what the data is. This may include information like where the data was originally hosted or how is was otherwise generated.
5. Upload the desired datasets to the release by using the file dialog in the release page (at time of writing in Firefox this is done by clicking "Attach binaries by dropping them here or selecting them." in the new release page).
6. Publish the release.
7. Add a description of the new data to this README in the "Available data" section. Include the full URL to access the data (for example "https://github.com/single-cell-data/TileDB-SOMA-Test-Data/releases/download/Visium-v2.0.0-Dataset/spatial.tar.gz")


Note: We are adding data directly to releases because we do not need the version-control functionality of Git for the test data, and GitHub has a larger file-size limit for release-artifact files than it does for files committed to source control within the repository.

## Access datasets

### General Access

The data can be downloaded by navigating to the release on GitHub or using `wget` or `curl` to access the data from the URL listed in this `README.md`.

### Add data to TileDB-SOMA

After you add a new dataset to this repository, you should add a sibling PR to access the data from TileDB-SOMA. More information about how to do this will be added to the `test/README.md` markdown file in the near future.
