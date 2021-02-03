# clone-readme

## Investigation

First, some files are missing in a respositry when run `git clone` with `actions/checkout@v2` on macOS using GitHub Action.
In conclete, see follow.

- Expected
  - .README
  - .README.md
  - .readme
  - .readme.md
  - README
  - README.md
  - README.md-haskell
  - README.md.haskell
  - README.rst
  - haskell-README.md
  - haskell-README.md.en
  - haskell-readme.md
  - haskell-readme.md.en
  - haskell.README.md
  - haskell.README.md.en
  - haskell.readme.md
  - haskell.readme.md.en
  - readme
  - readme.md
  - readme.md.en
- Actual
  - .readme
  - .readme.md
  - README.md-haskell
  - README.md.haskell
  - README.rst
  - haskell-readme.md
  - haskell-readme.md.en
  - haskell.readme.md
  - haskell.readme.md.en
  - readme
  - readme.md
  - readme.md.en

Diff of above, `diff Expected Actual`

```diff
1,2d0
< .README
< .README.md
5,6d2
< README
< README.md
10,11d5
< haskell-README.md
< haskell-README.md.en
14,15d7
< haskell.README.md
< haskell.README.md.en
```

But this causes on MacBook Air (Early 2015) with git(apple) and git(brew).
Why?

Let's try more simple pattern.

- Expected
  - README
  - README.md
  - readme
  - readme.md
- Actual
  - readme
  - readme.md

Diff of above, `diff Expected Actual`

```diff
1,2d0
< README
< README.md
```

Oh, left only small capital name files.
It this caused by case-insensitive file system?
Missed warning messages when runs `git clone` on macOS.

```
warning: the following paths have collided (e.g. case-sensitive paths
on a case-insensitive filesystem) and only one from the same
colliding group is in the working tree:

  'files/haskell-README.md.en'
  'files/haskell-readme.md.en'
  'files/haskell.README.md'
  'files/haskell.readme.md'
  'files/haskell.README.md.en'
  'files/haskell.readme.md.en'
  'files/README'
  'files/readme'
  'files/README.md'
  'files/readme.md'
```
