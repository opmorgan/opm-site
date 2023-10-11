Source code for [opmorgan.com](https://opmorgan.com)

## Dependencies
```hugo``` (v0.112.3+extended or later)
<br>
```python 3```
<br>
```bibtex-to-markdown``` ([https://github.com/opmorgan/bibtex-to-markdown](https://github.com/opmorgan/bibtex-to-markdown))

## To set up development environment

Build and run the server: 

```
hugo server -D
```


## To add publications

### Generate publication content for papers/ page
First, create a .bib file with publication(s) in bitex format (e.g., by exporting to biblatex from Zotero). Place the source .bib file in ```data/```.

Run academic (from [bibtex-to-markdown](https://github.com/opmorgan/bibtex-to-markdown)): 

```
academic import --bibtex data/[new-pub(s)].bib --publication-dir content/papers
```

This will generate .md files with publication info in `content/papers/[generated-pub-title]/[generated-pub-title].md`.

### Optional: add pdf
To host a pdf, place it in the same folder as `[generated-pub-title].md`, and add the file name (including the .pdf extension) to the .md file with the field `pdf_name`.  For example, if you add a file named `influential-paper_versionB.pdf` to the folder `content/papers/morgan-frequency/`, update the markdown file `content/papers/morgan-frequency/morgan-frequency.md` by adding the following line:

```
pdf_name: 'influential-paper_versionB.pdf'
```

### Optional: edit generated .md file
In addition to `pdf_name`, you can add these optional fields to the generated .md files. They will show up as links on the [sitename.com]/papers index page:
- `url_code: ''` (link to reproducible data and analysis code; link will be called "data & code")
- `url_dataset: ''` (link to dataset; link will be called "data")
- `url_press: ''` (link called "press")
- `url_task: ''` (link called "task script")
- `url_perma: ''` (permanent link to paper, useful if paper has no DOI; nonetheless, link will be called "doi").

The rendering of these fields is controlled in `layouts/papers/list.html`.



