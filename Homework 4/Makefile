BUILDDIR=build
FILE=homework4

pdf:
	mkdir $(BUILDDIR) -p
	pandoc $(FILE).md \
	--from=markdown+raw_tex+tex_math_single_backslash+tex_math_dollars \
	--to=latex \
	--output=$(BUILDDIR)/$(FILE).pdf \
	--pdf-engine=xelatex \
	--filter pandoc-citeproc \

clean:
	rm $(BUILDDIR)/*
