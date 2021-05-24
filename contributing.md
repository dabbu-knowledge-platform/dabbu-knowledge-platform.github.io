# Contributing to the documentation

First off, thanks for taking the time to contribute!

The following is a set of guidelines for contributing to the documentation. These are just guidelines, not rules, use your best judgment and feel free to propose changes to this document in a pull request.

## Issues

You can contribute to the documentation by reporting inconsistencies and suggesting improvements! If you want to report a bug, create an issue by clicking [here](https://github.com/dabbu-knowledge-platform/documentation/issues/new/choose).

## Pull requests

This guide assumes you are familiar with Github, Github Pages and the command line. If not, [here](https://guides.github.com) is a guide to get started with anything related to Github. If you are stuck on something, feel free to ask on [Github Discussions](https://github.com/dabbu-knowledge-platform/docs/discussions/categories/want-to-contribute).

### Step 0: Environment

Install `git` and `ruby`.

#### Git

`git` **must** be installed to make pull requests and push changed code.

- To check if git is already installed, type `git --version` in terminal/command prompt. You should see a version number displayed after running this command.
- [Here](https://github.com/git-guides/install-git) are the official instructions to install git for all platforms in case you haven't installed it already.

#### Ruby

`ruby` **must** be installed to preview your changes locally.

- To check if Ruby is already installed, type `ruby --version` in terminal/command prompt. You should see two version numbers displayed after running this command. For developing the documentation, we use version 2.7.3 of Ruby. **You may need a version manager like `rbenv and ruby-build` to install version 2.7.3**.
- [Here](https://www.ruby-lang.org/en/documentation/installation/#package-management-systems) are the official instructions to install NodeJS and Yarn for all platforms in case you haven't installed it already.

### Step 1: Fork

Fork the project [on the GitHub website](https://github.com/dabbu-knowledge-platform/docs) and clone your fork locally.

Run the following in a terminal to clone your fork locally:

```sh
$ git clone https://github.com/<your-username>/cli
$ cd cli
$ git remote add upstream https://github.com/dabbu-knowledge-platform/docs.git
$ git fetch upstream
```

### Step 2: Build

Run `bundle install` to install dependencies and `bundle exec jekyll serve` to run the site. If the command runs successfully, you will be able to see the site on `http://localhost:4000` in your browser.

Once you've built the project locally, you're ready to start making changes!

### Step 3: Branch

To keep your development environment organized, create local branches to hold your work. These should be branched directly off of the `develop` branch. While naming branches, try to name it according to the change it makes:

```sh
$ git checkout -b docs/add-cli-usage-instructions -t upstream/develop
```

### Step 4: Make changes

Make all the changes you want to the documentation!

- `index.md` contains an introduction to Dabbu Knowledge platform.
- `install.md` contains installation instructions.
- `setup-and-commands.md` contains a guide to introduce the user to the commands in Dabbu CLI.
- `api.md` contains the reference architecture diagram and links to the documentation of the Files and Intel API Servers.
- `legal.md` contains the license and code of conduct.

### Step 5: Commit

It is recommended to keep your changes grouped logically within individual commits. Many contributors find it easier to review changes that are split across multiple commits. There is no limit to the number of commits in a pull request.

```sh
$ git add my/changed/files
$ git commit
```

Note that multiple commits often get squashed when they are landed.

#### Commit message guidelines

A good commit message should describe what changed and why. This project uses [semantic commit messages](https://conventionalcommits.org/) to streamline
the release process.

Before a pull request can be merged, it **must** have a pull request title with a semantic prefix.

Examples of commit messages with semantic prefixes:

- `fix(perf): don't reload config everytime`
- `feat(copy): add copy command`
- `docs(readme): fix typo in readme.md`

Common prefixes:

- `fix`: A bug fix
- `feat`: A new feature
- `docs`: Documentation changes
- `perf`: A code change that improves performance
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `test`: A change to the tests
- `style`: Changes that do not affect the meaning of the code (linting)
- `build`: Bumping a dependency like node or express

Other things to keep in mind when writing a commit message:

- The first line should:
  - contain a short description of the change (preferably 50 characters or less, and no more than 72 characters)
  - be entirely in lowercase with the exception of proper nouns, acronyms, and the words that refer to code, like function/variable names
- Keep the second line blank.
- Wrap all other lines at 72 columns.

### Step 6: Rebase

Once you have committed your changes, it is a good idea to use `git rebase` (NOT `git merge`) to synchronize your work with the develop branch.

```sh
$ git fetch upstream
$ git rebase upstream/develop
```

This ensures that your working branch has the latest changes from `dabbu-knowledge-platform/docs` develop. If any conflicts arise, resolve them and commit the changes again.

### Step 7: Push

Once you have documented your code as required, begin the process of opening a pull request by pushing your working branch to your fork on GitHub.

```sh
$ git push origin docs/add-cli-usage-instructions
```

### Step 8: Opening the Pull Request

From within GitHub, opening a [new pull request](https://github.com/dabbu-knowledge-platform/docs/compare) will present you with a template that should be filled out.

### Step 9: Discuss and update

You will probably get feedback or requests for changes to your pull request. This is a big part of the submission process, so don't be discouraged! Some contributors may sign off on the pull request right away. Others may have detailed comments or feedback. This is a necessary part of the process in order to evaluate whether the changes are correct and necessary.

To make changes to an existing pull request, make the changes to your local branch, add a new commit with those changes, and push those to your fork. GitHub will automatically update the pull request.

```sh
$ git add my/changed/files
$ git commit
$ git push origin docs/add-cli-usage-instructions
```

There are a number of more advanced mechanisms for managing commits using `git rebase` that can be used, but are beyond the scope of this guide. Also, any branch that is being merged must be merged without fast forward, i.e., `git merge --no-ff ...`.

Feel free to post a comment in the pull request to ping reviewers if you are awaiting an answer on something.

**Approval and Request Changes Workflow**

All pull requests require approval from at least one maintainer in order to land. Whenever a maintainer reviews a pull request they may request changes. These may be small, such as fixing a typo, or may involve substantive changes. Such requests are intended to be helpful, but at times may come across as abrupt or unhelpful, especially if they do not include concrete suggestions on _how_ to change them.

Try not to be discouraged. Try asking the maintainer for advice on how to implement it. If you feel that a review is unfair, say so or seek the input of another project contributor. Often such comments are the result of a reviewer having taken insufficient time to review and are not ill-intended. Such difficulties can often be resolved with a bit of patience. That said, reviewers should be expected to provide helpful feedback.

### Step 10: Landing

In order to land, a pull request needs to be reviewed and approved by at least one maintainer. After that, if there are no objections from other contributors, the pull request can be merged.

**Congratulations and thanks a lot for your contribution!**
