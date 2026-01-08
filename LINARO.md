This is a soft fork of Zappa. It implements a few features specifically to aid the development and deployment of the Linaro Code Signing Service:

* Support for REQUEST authenticators.
* Support for custom authentication responses.

This fork tries to keep relatively in sync with Zappa. To do so, ensure that `git remote -v` displays this:

```
origin  git@github.com:linaro-its/linaro-zappa.git (fetch)
origin  git@github.com:linaro-its/linaro-zappa.git (push)
upstream        https://github.com/zappa/Zappa.git (fetch)
upstream        DISABLE (push)
```

If it doesn't, do this:

```
git remote add upstream https://github.com/zappa/Zappa.git
git remote set-url --push upstream DISABLE
```

To update the code, do this:

```
git fetch upstream
git checkout main
git merge upstream/master
git push origin main
```

Since this is a Python project, pay special attention to these files during the merge:

`requirements.txt` / `pyproject.toml`: If upstream added a library and you added a different one, you will get a conflict here. You usually want both.

`__init__.py`: Be careful here; ensure you don't overwrite your custom imports with the upstream's defaults.

Typically, the main difference might be in `__init__.py` if we have a custom version number.
