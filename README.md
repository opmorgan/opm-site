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


## To add papers

### Create and activate python environment (tested with python 3.13)

```python3 -m venv [env]```
```source env2/bin/activate```

### Install custom fork of academic-file-converter (formerly "hugo-academic-cli")

```pip3 install -U git+https://github.com/opmorgan/academic-file-converter.git```

This will enable you to run the ```academic``` command.

### Generate content for papers index page ([sitename.com]/papers)
First, create a .bib file with one or more publications in biblatex or bibtex format (e.g., by exporting to biblatex from Zotero). Place the source .bib file in ```data/```.

Then, convert the .bib entries to .md format, so that they can be rendered with Hugo:

```
academic import --bibtex data/[new-pub(s)].bib --publication-dir content/papers
```

This will generate .md files with publication info in `content/papers/[generated-pub-title]/[generated-pub-title].md`.

Manually edit the generated index.md file to make sure it looks how you want it to. For example:
- Check the author names and journal name
- Bold your author name by adding html tags (“<strong>[name]</strong>”)

### Optional: add pdf
To host a pdf, place it in the same folder as `[generated-pub-title].md`, and add the file name (including the .pdf extension) to the .md file with the field `pdf_name`.  For example, if you add a file named `influential-paper_versionB.pdf` to the folder `content/papers/morgan-frequency/`, update the markdown file `content/papers/morgan-frequency/morgan-frequency.md` by adding the following line:

```
pdf_name: 'influential-paper_versionB.pdf'
```

### Optional: add other optional fields to the generated .md file
In addition to `pdf_name`, you can add these optional fields to the generated .md files. They will show up as links on the [sitename.com]/papers index page:
- `url_code: ''` (link to reproducible data and analysis code; link will be called "data & code")
- `url_dataset: ''` (link to dataset; link will be called "data")
- `url_press: ''` (link called "press")
- `url_task: ''` (link called "task script")
- `url_perma: ''` (permanent link to paper, useful if paper has no DOI; nonetheless, link will be called "doi").

The rendering of these fields is controlled in `layouts/papers/list.html`.



