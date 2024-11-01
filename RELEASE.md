# Release Process

## Releasing a major or minor version.

1. Checkout the relevant commit and create a release branch having the format: `release-<MAJOR>.<MINOR`:

    ```bash
    MAJOR_MINOR="<MAJOR>.<MINOR>"
    git checkout -b release-${MAJOR_MINOR}
    ```

1. Push the release branch:

    ```bash
    git push upstream release-${MAJOR_MINOR}
    ```

1. Create and push the new tag with the correct patch version.

    ```bash
    MAJOR_MINOR_PATCH="<MAJOR>.<MINOR>.<PATCH>"
    git tag v${MAJOR_MINOR_PATCH}
    git push upstream v${MAJOR_MINOR_PATCH}
    ```

1. Build release artifacts locally using:

    ```bash
    goreleaser release --snapshot --clean
    ```

1. Using the [Github UI](https://github.com/kubernetes-sigs/gwctl/releases/new),
   create a new release using the newly created tag. Attach the release
   artifacts (only .tar and .zip files) generated in the previous step to the
   Release.
