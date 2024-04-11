# Bibtex Repo

Before adding entries to any of the files in the bibliography
repository, please carefully read the instructions at the beginning
of `literatur.bib`!

If you add conference papers of conferences which are likely to be
cited multiple times, please add cross reference entries in both
`crossref.bib` and `crossref-short.bib`. See also the instructions at
the beginning of these files.

## Usage

Within the main paper file, use

    \bibliography{abbrv,literatur,crossref}  # long versions
    \bibliography{abbrv-short,literatur,crossref-short}  # short versions
    \bibliography{abbrv,extra,literatur,crossref}  # if some citations are in extra.bib

To add the bibliography files to your paper repo, you can use the following Makefile target
(remember to indent with tabs):

    update-bib:
        for name in {abbrv-short,abbrv,literatur,crossref-short,crossref}; do \
            wget -q https://raw.githubusercontent.com/aibasel/bib/main/$${name}.bib -O $${name}.bib; \
            printf '\n%s\n\n%s\n' "% DO NOT EDIT THIS FILE DIRECTLY! It is overwritten by \"make update-bib\"." \
            "$$(cat $${name}.bib)" > $${name}.bib; \
        done

## Tests

You can run some basic tests on the bibliography files with

    ./tests/run-tests.sh

