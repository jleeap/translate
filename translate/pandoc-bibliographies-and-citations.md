# Bibliographies and Citations

## Bibliographies

### Specifying a Bibliography

[Pandoc](https://pandoc.org/MANUAL.html#citations) can automatically generate citations and a bibliography in a number of styles. In order to use this feature, you will need to specify a bibliography file using the `bibliography` metadata field in a YAML metadata section. For example:

```yaml
---
title: "Sample Document"
output: pdf_document
bibliography: bibliography.bib
---

```

If you are including multiple bibliography files, you can then define like this:

```yaml
---
bibliography: [bibliography1.bib, bibliography2.bib]
---

```

The bibliography may have any of these formats:

| Format      | File extension |
| ----------- | -------------- |
| BibLaTeX    | .bib           |
| BibTeX      | .bibtex        |
| Copac       | .copac         |
| CSL JSON    | .json          |
| CSL YAML    | .yaml          |
| EndNote     | .enl           |
| EndNote XML | .xml           |
| ISI         | .wos           |
| MEDLINE     | .medline       |
| MODS        | .mods          |
| RIS         | .ris           |

### Inline References

Alternatively you can use a `references` field in the document’s YAML metadata. This should include an array of YAML-encoded references, for example:

```yaml
---
references:
  - id: fenner2012a
    title: One-click science marketing
    author:
      - family: Fenner
        given: Martin
    container-title: Nature Materials
    volume: 11
    URL: "https://dx.doi.org/10.1038/nmat3283"
    DOI: 10.1038/nmat3283
    issue: 4
    publisher: Nature Publishing Group
    page: 261-263
    type: article-journal
    issued:
      year: 2012
      month: 3
---

```

### Bibliography Placement

Bibliographies will be placed at the end of the document. Normally, you will want to end your document with an appropriate header:

```markdown
last paragraph...

# References
```

The bibliography will be inserted after this header.

## Citations

### Citation Syntax

Citations go inside square brackets and are separated by semicolons. Each citation must have a key, composed of ‘@’ + the citation identifier from the database, and may optionally have a prefix, a locator, and a suffix. Here are some examples:

```
Blah blah [see @doe99, pp. 33-35; also @smith04, ch. 1].

Blah blah [@doe99, pp. 33-35, 38-39 and *passim*].

Blah blah [@smith04; @doe99].
```

A minus sign `(-)` before the `@` will suppress mention of the author in the citation. This can be useful when the author is already mentioned in the text:

```
Smith says blah [-@smith04].
```

You can also write an in-text citation, as follows:

```
@smith04 says blah.

@smith04 [p. 33] says blah.
```

### Unused References (nocite)

If you want to include items in the bibliography without actually citing them in the body text, you can define a dummy `nocite` metadata field and put the citations there:

```
---
nocite: |
  @item1, @item2
...

@item3
```

In this example, the document will contain a citation for `item3` only, but the bibliography will contain entries for `item1`, `item2`, and `item3`.

### Citation Styles

By default, pandoc will use a Chicago author-date format for citations and references. To use another style, you will need to specify a CSL 1.0 style file in the `csl` metadata field. For example:

```yaml
---
title: "Sample Document"
output: pdf_document
bibliography: bibliography.bib
csl: biomed-central.csl
---

```

A primer on creating and modifying CSL styles can be found [here](https://citationstyles.org/downloads/primer.html). A repository of CSL styles can be found [here](https://github.com/citation-style-language/styles). See also https://zotero.org/styles for easy browsing.

### Citations for PDF Output

By default, citations are generated by the utility pandoc-citeproc, and it works for all output formats. When the output is LaTeX/PDF, you can also use LaTeX packages (e.g. natbib) to generate citations; see [PDF documents](pandoc-pdf.md) for details.