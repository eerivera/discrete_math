SOURCES := parse-tree.tex parse-tree-evaluation.tex
OUTPUT_DIR := ../../images/F01
BUILD_DIR := build
SVGS := $(SOURCES:%.tex=$(OUTPUT_DIR)/%.svg)

.PHONY: all clean

all: $(SVGS)

$(OUTPUT_DIR)/%.svg: %.tex parse-tree-style.tex
	mkdir -p $(BUILD_DIR) $(OUTPUT_DIR)
	latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=$(BUILD_DIR) $<
	pdftocairo -svg $(BUILD_DIR)/$*.pdf $@

clean:
	latexmk -C -outdir=$(BUILD_DIR)
