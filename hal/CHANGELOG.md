# Change Log

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](http://keepachangelog.com/).
> Sections: (`Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`, `API Changes`, `Entity Changes`)

## [dev] - 2020-06-XX

### Added
- Added `hal/publish` job.
  > This job is used to publish a build and transfer an artifact from CircleCI to Hal. Do not use
  > if no artifact is passed to Hal (Use `hal/build`).
  >
  > Usage example:
  > ```
  > TBD
  > ```
- Added `hal/checkout` job.
  > This is a simple job that is only used to check out code and persist those files.
  > Projects should typically checkout only once, and pass those files in workspaces to further jobs in the pipeline.
  >
  > Usage example:
  > ```
  > TBD
  > ```
