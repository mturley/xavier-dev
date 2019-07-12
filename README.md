# xavier-dev

This repo contains scripts and instructions to help developers and stakeholders of the Migration Analytics cloud services UI (upstream name "project-xavier") to set up and run the UI development environment and view changes before they are deployed.

# Setup for macOS:

Open a Terminal and run the following commands.

First, install Homebrew:
```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Then, use Homebrew to install git:
```sh
brew install git
```

Then, use git to clone this repository and run its setup script:

```sh
git clone https://github.com/mturley/xavier-dev.git
cd xavier-dev
bin/setup-mac
```

You may be asked for your macOS password to install dependencies.

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

# Updating with new changes from GitHub:

This will update and rebuild the environment from the current branch in each repo.

```sh
cd xavier-dev
bin/update
```

# Viewing changes in a PR:

You can view changes not yet merged to master by fetching and checking out the relevant branch.

Before you do this, you'll need to add the git remote for the person whose PR you want to view.
For example, to add Mike's and Carlos' remotes (do this once):

```sh
cd xavier-dev/src/xavier-ui
git remote add carlos https://github.com/carlosthe19916/xavier-ui.git
git remote add mike https://github.com/mturley/xavier-ui.git
```

To look at a PR's changes, first you need to know what branch to view and where to fetch it from. You can find out which branch relates to a PR by looking at the line below a PR's title on GitHub. For example, if you look at https://github.com/project-xavier/xavier-ui/pull/22, the line "carlosthe19916 wants to merge 64 commits into project-xavier:master from carlosthe19916:sprint1" indicates that this PR is on the branch `sprint1`.

Let's say you want to view the changes on Carlos' branch called `sprint1`. You'd fetch Carlos' remote, then checkout the branch, then run the update script.
```sh
cd xavier-dev/src/xavier-ui
git fetch carlos
git checkout sprint1
cd ../..
bin/update
```

Note that you'll stay on Carlos' `sprint1` branch until you switch back to `master`, by doing the same as above and using `git checkout master` instead of `git checkout sprint1`.
