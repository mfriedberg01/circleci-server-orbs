# Change Log

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](http://keepachangelog.com/).
> Sections: (`Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`, `API Changes`, `Entity Changes`)

## [dev] - 2020-06-XX

### Added
- Added job: `hal/checkout`
  > This is a simple job that is only used to check out code and persist those files.
  > Projects should typically checkout only once, and pass those files in workspaces to further jobs in the pipeline.
  >
  > Usage example:
  >
  > ```
  > orbs:
  >     hal: quickenloans/hal@x.y.z
  > workflows:
  >     my_example_pipeline:
  >         jobs:
  >             - hal/checkout:
  >                 workspace-root: '.' # Default value (can be deleted)
  >                 persist-path: '.'   # Default value (can be deleted)
  > ```
- Added job: `hal/publish`
  > This job is used to publish a build and transfer an artifact from CircleCI to Hal. Do not use
  > if no artifact is passed to Hal (Use `hal/build`).
  >
  > Usage example:
  >
  > ```
  > orbs:
  >     hal: quickenloans/hal@x.y.z
  > workflows:
  >     my_example_pipeline:
  >         jobs:
  >             - hal/publish:
  >                 requires: [ hal/checkout ]
  >                 context: 'my_secrets'
  >
  >                 hal-appid: '000000'
  >                 workspace-root: '.'        # Default value (can be deleted)
  >                 job-file: '.hal_build_id'  # Default value (can be deleted)
  >                 artifact-path: './mybuildfiles'
  >                 artifact-compression: 'tgz'
  > ```
- Added job: `hal/build`
  > This job is used to start a build. Do not use if an artifact is need to be passed to Hal (Use `hal/publish`).
  >
  > Usage example:
  >
  > ```
  > orbs:
  >     hal: quickenloans/hal@x.y.z
  > workflows:
  >     my_example_pipeline:
  >         jobs:
  >             - hal/publish:
  >                 requires: [ hal/checkout ]
  >                 context: 'my_secrets'
  >
  >                 hal-appid: '000000'
  >                 workspace-root: '.'        # Default value (can be deleted)
  >                 job-file: '.hal_build_id'  # Default value (can be deleted)
  >                 artifact-path: './mybuildfiles'
  >                 artifact-compression: 'tgz'
  > ```
- Added command: `hal/install-certificates`
  > This command is used to install company certificates for access to APIs or Applications that use an Internal CA for SSL.
  >
  > Usage example:
  >
  > ```
  > orbs:
  >     hal: quickenloans/hal@x.y.z
  > jobs:
  >     my_example_job:
  >         steps:
  >             - hal/install-certificiates
  > ```
