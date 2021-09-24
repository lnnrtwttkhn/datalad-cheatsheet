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

## Errors

### Transfer already in progress

#### What?

```
transfer already in progress, or unable to take transfer lock; Unable to access these remotes: origin; Try making some of these repositories available
```

#### Fix?

- `rm -rf ./.git/annex/transfer/` (see [here](https://git-annex.branchable.com/forum/How_to_fix__58_____40__transfer_already_in_progress__44___or_/#comment-84a8489f52db87674fd256cfe68ab040))

#### Why?

- Did you cancel e.g., a `datalad get` operation with `ctrl` + `c`?

#### References

- https://git-annex.branchable.com/forum/How_to_fix__58_____40__transfer_already_in_progress__44___or_/
- https://github.com/datalad/datalad/issues/2768
- https://github.com/datalad/datalad/issues/5589
