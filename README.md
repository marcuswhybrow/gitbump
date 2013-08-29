# Git Bump

## Install it!

    sudo wget -O /usr/local/bin/gitbump http://git.io/rnTHRQ

## Give Git Bump What it Wants

Git Bump expects two things: A tag in the [semver](http://semver.org/) format (ex: 1.25.3) and a tag called "latest" that points to your latest version tag. To set this up first time you can do:

    git tag -a 0.0.0 -m "Version 0.0.0"
    git tag -a latest -m "Latest recommended version (0.0.0)"

## Usage

    gitbump          # Bump the patch version (right most number)
    gitbump patch    # Same as before (the explicit approach)
    gitbump minor    # Bump the minor version (the middle number)
    gitbump major    # Bump the major version (yup: the left most number)