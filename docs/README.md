# These are the docs

The docs are hosted on https://mpd-album-art-grabber.readthedocs.org

If you wish to build the docs yourself, there are a bunch of make targets you
can choose from:

For all cases, make sure to change directory to docs/
```
cd docs
```

## Make the text
```sh
make text
```
will output generated text files to `docs/_build/text/`

## Make the html
```sh
make html
```
will output generated html files to `docs/_build/html`

## Run the inline code snippets in the docstrings
```sh
make doctest
```
will output results from the test to `docs/_build/doctest/output.txt`
