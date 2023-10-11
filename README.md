Source code for [opmorgan.com](https://opmorgan.com)

## Dependencies
```hugo``` (v0.112.3+extended or later)

```python 3```

```bibtex-to-markdown``` ([https://github.com/opmorgan/bibtex-to-markdown](https://github.com/opmorgan/bibtex-to-markdown))

## To set up development environment

Build and run the server: ```hugo server -D```


## To add publications

First, create a .bib file with publication(s) in bitex format (e.g., by exporting to biblatex from Zotero). Place the source .bib file in ```data/```.

Activate python venv: ```source env/bin/activate```

Run academic (from [bibtex-to-markdown](https://github.com/wowchemy/bibtex-to-markdown)): ```academic import --bibtex data/[new-pubs].bib --publication-dir content/papers```

Edit generated .md files in ```content/papers/```.


