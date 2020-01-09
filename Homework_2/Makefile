BUILDDIR=build
FILE=homework2

pdf:
	mkdir $(BUILDDIR) -p
	pandoc $(FILE).md \
	--from=markdown+raw_tex+tex_math_single_backslash+tex_math_dollars \
	--to=latex \
	--output=$(BUILDDIR)/$(FILE).pdf \
	--pdf-engine=xelatex \
	--variable urlcolor=cyan \
	--variable papersize=a4paper \
	--filter pandoc-citeproc \
	--bibliography=bibliography.bib \
	--csl=https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl \

# --csl=https://www.zotero.org/styles/frontiers-in-applied-mathematics-and-statistics \

clean:
	rm $(BUILDDIR)/*
