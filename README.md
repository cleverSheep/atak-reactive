fork of https://github.com/rixau/atak-reactive with offline support

prerequisites for runnning offline:

- The required dependency versions must already exist in your local Gradle cache (~/.gradle/caches/modules-2/files-2.1/...) from a prior successful build. Offline mode cannot resolve anything not already cached.
- Dynamic/range versions (e.g. 3.+, [5.4.0-SNAPSHOT, 5.4.1-SNAPSHOT)) may still fail offline even with a cached artifact present, since Gradle needs a version listing from the remote to resolve the range. This has caused release-variant builds to fail with No cached version listing ... available for offline mode — if you hit this, build the debug flavor instead (assembleMilDebug), which doesn't pull in the affected coreRules config.

one-time setup:

in the atak-reactive CLI repo:

`cd path\to\atak-reactive\cli`

`npm install`

`npm run build`

`npm link`

in the plugin project's web/ folder:

`cd path\to\atak-plugin\web`

`npm link @atak-reactive/cli`

from the plugin project web folder:

`npm run dev -- --flavor mil --offline`

to unlink (later) -> `npm unlink @atak-reactive/cli && npm install` in web/
