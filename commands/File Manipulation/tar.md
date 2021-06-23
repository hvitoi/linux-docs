# tar

- Tape Archive
- Tar is a bundle of files, creating a tarball
- It's not compressed!

## Tar

```bash
# TAR
tar -cvf `file.tar` `file-folder-1` `file-folder-2` `file-folder-3`
tar -cvf tarball.tar .
tar -cvf tarball.tar mytext.txt mydiary2.txt myfolder myfoldertwice
# c - create
# v - verbose (display progress)
# f - specify a file output name

# TAR and COMPRESS
tar -czvf `file.tar.gz` `file-folder`  # z - GZIP .tar.gz .tgz
tar -cjvf `file.tar.gz` `file-folder` # j - BZIP2 .tar.bz2 .tar.bz .tbz

# Exclude files
tar -czvf `file.tar.gz` `file-folder` --exclude=`file-folder-excluded`
tar -czvf tarball.tar.gz /home/eu --exclude=*.mp4
```

## Untar

```bash
# UNTAR
tar -xvf `file` # Extracts to current folder
tar -xvf `file` -C `destination` # Extract to a destination
tar -xvf tarball.tar -C /tmp

# UNTAR and UNCOMPRESS
tar -xzvf `file` # gzip
tar -xjvf `file` # bzip2
tar -xJxvf `file` # xz
```

## Other

```shell
# Strip
tar -xzvf `file.tgz` --strip-components=1
```
