## How to setup and build

1. Install [`depot_tools`](https://commondatastorage.googleapis.com/chrome-infra-docs/flat/depot_tools/docs/html/depot_tools_tutorial.html#_setting_up) (ensure they're on your `PATH`).
2. `git clone https://github.com/motiz88/rn-chrome-devtools-buildscripts`
3. `cd rn-chrome-devtools-buildscripts`
4. `gclient sync --no-history`
5. For local development, you may at this point delete the `devtools-frontend` directory, create a symlink to your [`rn-chrome-devtools-frontend`](https://github.com/motiz88/rn-chrome-devtools-frontend) checkout in its place, and run `gclient sync --no-history` again.
6. `cd devtools-frontend`
7. Generate Ninja build files: `gn gen out/Default`
8. Build: `autoninja -C out/default`

## Running a build of Chrome DevTools in hosted mode

1. Start a static web server: `python3 -m http.server 8000 --directory out/Default/gen/front_end`
2. The frontend is available at `http://localhost:8000/inspector.html`. You can connect this frontend to a target by adding the `?ws=` parameter (take its value from the target's `devtoolsFrontendUrl`).

See https://github.com/ChromeDevTools/devtools-frontend/blob/main/docs/workflows.md for more general information about development workflows in the Chrome DevTools codebase.
