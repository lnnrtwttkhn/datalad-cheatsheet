# DataLad Cheatsheet

## Create `rclone special remote`

```bash
RCLONE_REMOTE=<name_of_your_rclone_remote>
git annex initremote ${RCLONE_REMOTE} type=external externaltype=rclone chunk=50MiB encryption=none target=${RCLONE_REMOTE}
```

## Configure publication dependency on sibling

```bash
datalad siblings add -s origin --url git@git.mpib-berlin.mpg.de:wittkuhn/zoo-glm.git --publish-depends keeper
```

## Change URL of subdataset

```bash
datalad subdatasets --contains midterm_project --set-property url https://github.com/adswa/midtermproject
```

## Change dataset permissions to be able to delete it

[Reference](http://handbook.datalad.org/en/latest/basics/101-136-filesystem.html#deleting-a-superdataset)

```bash
chmod -R u+w <dataset>
```
