#!/usr/bin/make -f

.PHONY: Documentation.pdf all clean

# Variables
temp-dir = Temp
ok = [OK]

# Functions
tempfile = ${temp-dir}/${1}
latexmk = @latexmk -pdf -xelatex -shell-escape -use-make --output-directory=${temp-dir} ${1}
xelatex = @xelatex -shell-escape --output-directory=${temp-dir} ${1}
pdfetex = @pdfetex -shell-escape -output-directory=${temp-dir} ${1}
biber = @biber $(call tempfile,$1)

copy = cp $(call tempfile,$1).pdf .
cleanLatex = @latexmk --output-directory=${temp-dir} -CA
clean = @rm ${temp-dir}/*

define build = 
$(call latexmk,$1)
$(call copy,$1) 
endef

all: Documentation.pdf

clean:
	$(call clean)
	@echo ${ok}

Documentation.pdf: Documentation.tex
	$(call htlatex,Documentation)
	@echo ${ok}

