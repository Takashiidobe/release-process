# Example Release Process

We have two projects, Backend and Frontend. Backend is always deployed before Frontend.

## Backend Release Process

- Make sure any changes for this release are merged into the master branch.
- Tag current master following Semver policy. Increment the patch version for a bug fix release, increment the minor version for a backwards compatible feature release, and increment the major version for a backwards incompatible release.
- Then, deploy the project in AWS. Codebuild will deploy the project to our EC2 instances.
  - If the build fails, figure out if this was due to a problem in AWS, or the code.
  - If the build succeeds, then wait for all instance traffic to move to the new instances before moving onto the Frontend release.

## Frontend Release Process

- Make sure any changes for this release are merged into the master branch.
- Tag current master following Semver policy. Increment the patch version for a bug fix release, increment the minor version for a backwards compatible feature release, and increment the major version for a backwards incompatible release.
- Deploy to staging on netlify.
- Allow all tests to run through Percy on staging to make sure there are no UI related regressions on all supported platforms.
- Deploy to production on netlify.
