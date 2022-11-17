# Auto Change Log Testing

## `standard-version`

### Install

```sh
yarn add -D standard-version
```

### Release

```sh
# initial release
yarn standard-version --first-release

# release method
yarn standard-version # 0.0.1(patch)
yarn standard-version --release-as minor # 0.1.0 (minor)
yarn standard-version --release-as major # 1.0.0 (major)
yarn standard-version --release-as [version-to-release]
```

### Other Packages
