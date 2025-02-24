# soma-experiment-versions

Locate the [`ingestor` script](https://github.com/single-cell-data/TileDB-SOMA/blob/1.15.7/apis/python/devtools/ingestor).

Alternatively, make your own:

```
#!/usr/bin/env python
import tiledbsoma.io
import sys
tiledbsoma.io.from_h5ad(
    sys.argv[2], // output TileDB-SOMA Experiment URI
    sys.argv[1], // input .h5ad path
    measurement_name="RNA",
    X_layer_name="data",
)
```

Get the two PBMC inputs:

```
$ aws s3 ls s3://tiledb-unittest/soma-prod-test-data/h5ad/
2025-02-06 13:23:57   40213490 pbmc3k_processed.h5ad
2025-02-06 13:23:50   28197068 pbmc3k_unprocessed.h5ad
```

Copy them to local:

```
$ aws s3 cp s3://tiledb-unittest/soma-prod-test-data/h5ad/pbmc3k_processed.h5ad .
$ aws s3 cp s3://tiledb-unittest/soma-prod-test-data/h5ad/pbmc3k_unprocessed.h5ad .
```

Ingest these with various TileDB-SOMA versions:

```
version=1.7.3
version=1.12.3
version=1.14.5
version=1.15.0
version=1.15.7
```

For each version:

```
pip uninstall -y tiledbsoma
pip install tiledbsoma==$version
# For 1.7.3, 1.12, 1.14.5:
pip install anndata==0.10.9
# Otherwise:
pip install anndata==0.11.3
```

```
mkdir soma-experiment-versions
mkdir soma-experiment-versions/$version
```

```
ingestor.py pbmc3k_unprocessed.h5ad soma-experiment-versions/$version/pbmc3k_unprocessed
ingestor.py pbmc3k_processed.h5ad   soma-experiment-versions/$version/pbmc3k_processed
```

Once all versions are complete, expect output such as:

```
ubuntu@geras[prod][][v]$ ls -l soma-experiment-versions/
total 24
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 24 17:11 1.12.3
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 24 17:11 1.14.5
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 24 17:11 1.15.0
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 24 17:11 1.15.7
drwxrwxr-x 4 ubuntu ubuntu 4096 Feb 24 17:11 1.7.3
drwxrwxr-x 2 ubuntu ubuntu 4096 Feb 24 17:11 h5ad
```

```
ubuntu@geras[prod][][v]$ ls -l soma-experiment-versions/*/
soma-experiment-versions/1.12.3/:
total 8
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_processed_1.12.3
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_unprocessed_1.12.3

soma-experiment-versions/1.14.5/:
total 8
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_processed_1.14.5
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_unprocessed_1.14.5

soma-experiment-versions/1.15.0/:
total 8
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_processed_1.15.0
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_unprocessed_1.15.0

soma-experiment-versions/1.15.7/:
total 8
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_processed_1.15.7
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_unprocessed_1.15.7

soma-experiment-versions/1.7.3/:
total 8
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_processed_1.7.3
drwxrwxr-x 6 ubuntu ubuntu 4096 Feb 24 17:13 pbmc3k_unprocessed_1.7.3

soma-experiment-versions/h5ad/:
total 66812
-rw-rw-r-- 1 ubuntu ubuntu 40213490 Feb  6 18:23 pbmc3k_processed.h5ad
-rw-rw-r-- 1 ubuntu ubuntu 28197068 Feb  6 18:23 pbmc3k_unprocessed.h5ad
```

Then:

```
tar zcf soma-experiment-versions.tgz soma-experiment-versions
```
