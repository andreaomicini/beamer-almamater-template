# beamer-almamater-template

> A ready-to-use presentation skeleton for the
> [almamater](https://github.com/andreaomicini/beamer-almamater) Beamer style, built once per preset

## author

* Andrea Omicini

## usage

Copy `almamater-template.tex` and `almamater-template.bib`, and start from there. The file builds as
the `AMSUniBo` preset; any other preset is one definition away:

```bash
latexmk -pdf almamater-template.tex                                     # AMSUniBo
latexmk -pdf -jobname=almamater-template-AMSCesena \
  -usepretex='\def\almamaterpreset{AMSCesena}' almamater-template.tex   # AMSCesena
```

In a deck of your own, name the preset directly: `\usetheme{AMSCesena}`.

## structure

| file | what it is |
| --- | --- |
| `almamater-template.tex` | the template: every frame the six presets share |
| `presets/<Preset>/` | what one preset brings: `options.tex` (its seal, read before `\documentclass`), `preamble.tex` (its title and the swatch helpers in its colours), and the frames that show its colours — `ams`, `aim`, `colours`, `palette`, `surfaces`, `citations`, `urls`, `doi`, `apice-addresses`, `alert-emphasis`, `speakers`, `seal-options` |
| `almamater-template.bib` | the bibliography, one real APICe record for each entry type the style handles |
| `.style` | the style, `beamer-almamater`, as a submodule; `.latexmkrc` puts all of it on the search path |
| `ci/` | the release scripts |

Until 2.0.0 there were six template repositories, one per style (`beamer-AMSUniBo-template` …); this
one was assembled from them on 2026-11-08: the frames identical in all six became the shared file, every
frame that differed went whole into its preset's folder. Each preset's PDF reads as its old template
did, but for the version and the four frames that now name `almamater`.

## CI

Every push to `main` that changes the template builds it six times (`-usepretex`, one per preset) and
releases the six PDFs together, `almamater-template.zip`, here and on GitHub.

## licence

The template is released into the public domain under [CC0 1.0 Universal](LICENSE); the style it uses
is covered by its own licence (LPPL 1.3c).
