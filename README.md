# install.opensource.sh
install.opensource.sh is simple one-line installer for command line tools and stuff.

You can integrate install.opensource.sh with your existing public GitHub repos or if you want to install some secret things you can use it with Secret Gists for instance. See how it works on the section below.

Usage example:

```sh
sh <(curl -sL http://install.opensource.sh/github_user/repo) --args
```

## How it works?

There are 2 ways to use `install.opensource.sh` for your projects.

### With public GitHub repos

If you want to use it for your public projects on GitHub the only thing you have to do is to create file in your repo with name `install.opensource.sh`

```sh
cd my_repo
echo "echo 'Hello World from install.opensource.sh'" > install.opensource.sh
git add .
git commit -am "Enable install.opensource.sh for my project"
git push
```

To test it whether it works try this command:

```sh
$ sh <(curl -sL http://install.opensource.sh/githubuser/my_repo)
Hello World from install.opensource.sh # this should be the result
```

There are few exmaples with public GitHub repos
- https://github.com/mignev/develo/blob/master/install.opensource.sh
- https://github.com/mignev/install.sh/blob/master/install.opensource.sh
- https://github.com/sappio/dot/blob/master/install.opensource.sh


### For private stuff via GitHub Gists

The way of using GitHub Gists is very similar to GitHub public repos. In your private Gist you have to create a file with name `install.opensource.sh` and there you have to put your logic :) That's it basically :)

There are some additional things for Gists that you have to know. I'am talking about hooks and files in Gist

#### Hooks
- `pre.install.opensource.sh`
- `post.install.opensource.sh`

From the names of these hooks you can realize that the logic in `pre.install.opensource.sh` will be executed right before logic in `install.opensource.sh` and `post.install.opensource.sh` right after. That's it ... no more.

#### Files

You can create additional files in your gists of course but the only thing that you have to know is that `install.opensource.sh` will create TMP directory and will download all files from your gist there (except install.opensource.sh and the hooks).

The name of the TMP directory will be stored in Environment variable with name `INSTALL_TMP_DIR` and you can use it from `install.opensource.sh` and from all the hooks.

This is a simple example of a Secret Gist:
- https://gist.github.com/mignev/2dbf13fdd96e462782e5

#### Installing the Gist
This is the command for installation you your gist

```sh
sh <(curl -sL http://install.opensource.sh/gist/:gist_id)
```

You can try with the secret gist that I gave you as an example:

```sh
sh <(curl -sL http://install.opensource.sh/gist/2dbf13fdd96e462782e5)
```

### Passing arguments to `install.opensource.sh`

if you want to pass some arguments to the installer ... this is the way you can do it:

```sh
sh <(curl -sL http://install.opensource.sh/github_user/repo) -a value --arg1 value
```

## Command line tool

There is another way to interact with http://install.opensource.sh via `install.sh` tool.

Installation is very easy :)

```
sh <(curl -sL http://install.opensource.sh/)
```

Installation of GitHub repo project

```sh
install.sh github_user/repo
```

Installation of GitHub Gists

```sh
install.sh gist/:gist_id
```

You can find more info for `install.sh` [here](https://github.com/mignev/install.sh)

## Related projects
- [install.sh](https://github.com/mignev/install.sh)
- [pkgsh](https://github.com/pkgsh)

## TODO
- add info for package file
- add info for packages organization and repos
