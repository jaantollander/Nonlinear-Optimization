BUILDDIR=build
FILE=report

pdf:
	mkdir $(BUILDDIR) -p
	pandoc $(FILE).md \
	--from=markdown+raw_tex+tex_math_single_backslash+tex_math_dollars \
	--to=latex \
	--output=$(BUILDDIR)/$(FILE).pdf \
	--pdf-engine=xelatex \
	--filter pandoc-citeproc

tex:
	mkdir $(BUILDDIR) -p
	pandoc $(FILE).md \
	--from=markdown+raw_tex+tex_math_single_backslash+tex_math_dollars \
	--to=latex \
	--output=$(BUILDDIR)/$(FILE).tex \
	--filter pandoc-citeproc

clean:
	rm $(BUILDDIR)/*
