# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Displaying mkdocs.yml

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

~~~text
    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
~~~

## Deploy to Github

~~~sh

#!/bin/bash

# Check if a site name is provided
if [ -z "$1" ]; then
  echo "Usage: $0 <site_name>"
  exit 1
fi

SITE_NAME=$1
PROJECT_DIR="/home/larry/mk/$SITE_NAME"

# Step 1: Navigate to project directory
cd "$PROJECT_DIR" || { echo "❌ Directory not found!"; exit 1; }

# Step 2: Activate virtual environment
source venv/bin/activate

# Step 3: Deploy MkDocs site
mkdocs gh-deploy --force

echo "✅ MkDocs site deployed for $SITE_NAME! Live at: https://blutterfly.github.io/$SITE_NAME/"
~~~
