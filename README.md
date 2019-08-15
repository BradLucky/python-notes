# Table of Contents

* [Python Notes](#python-notes)
* [Git Notes](#git-notes)
* [Rapid Grep Notes](#rapid-grep-notes)

# Python Notes
A cheat sheet for less-used Python tools and methods

## Timing Python
```python
import timeit


timeit.timeit("""
    name = 'Brad'
    age = 90
    f'{name} is {age} years old.'
""")

>>> 0.15161066000291612

timeit.timeit("""
    name = 'Brad'
    age = 90
    '{} is {} years old'.format(name, age)
""")

>>> 0.3390180559945293
```

## Advanced formatting with f-strings
```python
name = 'Brad'

f'{name.center(10, "*"):~^20}'
>>> '~~~~~***Brad***~~~~~'

f'{name.center(10, "*"):~>20}'
>>> '~~~~~~~~~~***Brad***'

f'{name.center(10, "*"):~<20}'
>>> '***Brad***~~~~~~~~~~'
```

## Arrow vs. CISO8601
For reference CISO8601 is considerably faster, but...
```python
ciso8601.parse_datetime(<DateTime>) == arrow.get(<DateTime>).datetime
```

# Git Notes

## Revert a committed change
Use this with caution. It will erase all history of commits after the hash you use.
```bash
$ git reset --hard <hash>
```

## Squashing commits (before pushing)
```bash
$ git rebase -i development  # branch name
```
In the editor that comes up, change "most" lines to `squash` and save.

Update the commit message as desired.
```bash
$ git push --force
```

## Starting with git-lint

1. Delete git-lit cache
2. Remove the `REPO_HOME` line

# Rapid Grep Notes

## Exclude a directory from search

```bash
$ rg template -g '!frontend/*'
```
