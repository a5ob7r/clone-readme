# clone-readme

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
