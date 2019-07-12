# xavier-dev
Helper scripts to quickly setup and run the xavier-ui dev environment

# Setup for macOS:

```sh
git clone git@github.com:mturley/xavier-dev.git
cd xavier-dev
bin/setup-mac
```

# Running the environment:

* Open 4 terminal windows/tabs
* Navigate them all to this directory (`cd xavier-dev`)
* Run each the following commands in one of the terminal windows:
  ```sh
  bin/insights-chrome
  bin/insights-proxy
  bin/jaxrs-util-mocks
  bin/xavier-ui
  ```
* Open your browser to https://ci.foo.redhat.com:1337/staging/migration-analytics
