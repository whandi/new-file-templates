# This file still needs work, but should work for single-target latex builds
# make sure to set MAIN_TEX and MAIN variables to reasonable values for your
# project

MAIN_TEX = document.tex
MAIN = document.pdf

TEX = latexmk
LATEX = -pdflatex="pdflatex -interaction=nonstopmode"
TEX_OPTIONS = -pdf -use-make --deps "$(MAIN_TEX)" -deps-out=".deps" -file-line-error

.PHONY: all
all: Makefile
all: $(MAIN)

$(MAIN): $(MAIN_TEX)
	$(TEX) $(TEX_OPTIONS) $(LATEX) $(MAIN_TEX)
	
.PHONY: continuously
continuously:
	$(TEX) $(TEX_OPTIONS) -pvc $(LATEX) $(MAIN_TEX)

-include .deps

#.PHONY: continuously
#continuously:
#	$(TEX) $(TEX_OPTIONS) -pvc $(LATEX) $(MAIN_TEX)

.PHONY: clean
clean:
	@latexmk -CA
	@rm -f $$(find . -type f -name *.aux)
	@rm -f $$(find . -type f -name *.fls)
	@rm -f $$(find . -type f -name *.log)
	@rm -f $$(find . -type f -name *.tex.swo)
	@rm -f $$(find . -type f -name *.fdb_latexmk)
	@rm -f .deps
	@rm -f *.synctex.z
	@rm -f $$(find . -type f -name *.swp)
	
