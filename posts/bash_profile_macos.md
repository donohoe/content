# _bash_profile_ for macOS
#### March 11th 2022

Rather than re-inventing this every few months, or years, I'm sticking it here for posterity. Nothing here is sensitive.

`vi ~/.bash_profile`

## The file

```bash

# Library Paths
# =====================
# These variables tell your shell where they can find certain
# required libraries so other programs can reliably call the variable name
# instead of a hardcoded path.

# NODE_PATH

# Node Path from Homebrew I believe
export NODE_PATH="/usr/local/lib/node_modules:$NODE_PATH"

# Paths
# =====================

export PATH="$USR_PATHS:$PATH"

# Configurations
# =====================

# GIT_MERGE_AUTO_EDIT
# This variable configures git to not require a message when you merge.
export GIT_MERGE_AUTOEDIT='no'

# Helpful Functions
# =====================

# This function is called in your prompt to output your active git branch.
function parse_git_branch {
  git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# A function to CD into the desktop from anywhere so you just type desktop.
# HINT: It uses the built in USER variable to know your OS X username

# USE: desktop
#      desktop subfolder
function desktop {
  cd /Users/$USER/Desktop/$@
}

# USE: themes OR plugins OR projects OR wordpress directories
function themes {
  cd /Users/$USER/Development/localwp/app/public/wp-content/themes/$@
}
function plugins {
  cd /Users/$USER/Development/localwp/app/public/wp-content/plugins/$@
}
function projects {
  cd /Users/$USER/Development/localwp/app/public/wp-content/projects/$@
}
function wordpress {
  cd /Users/$USER/Development/localwp/app/public/$@
}

# Aliases
# =====================

# LS
alias ll='ls -lah'

# Starting directory
# =====================
cd /Users/$USER/Development/
```
