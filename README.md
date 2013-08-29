# gitbump

Sometimes one needs a tag that always points to the same commit as your latest realease tag. Now bumping your version number is a pain. `gitbump` increments the major, minor or patch number by one and updates `latest` too.

### Install it!

    sudo wget -O /usr/local/bin/gitbump http://git.io/rnTHRQ

### Give gitbump What it Wants

`gitbump` expects two things: A tag in the [semver](http://semver.org/) format (ex: `1.25.3`) and a tag `latest` that points to the same commit as your latest version tag. To set this up first time you can do:

    git tag -a 0.0.0 -m "Version 0.0.0"
    git tag -a latest -m "Latest recommended version (0.0.0)"

### Usage

    gitbump          # Bump the patch version (right most number)
    gitbump patch    # Same as before (the explicit approach)
    gitbump minor    # Bump the minor version (the middle number)
    gitbump major    # Bump the major version (yup: the left most number)