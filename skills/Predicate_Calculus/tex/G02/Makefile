SOURCES := practice-truth-tree.tex quantifier-valid.tex soccer-tree.tex
OUTPUT_DIR := ../../images/G02
BUILD_DIR := build
SVGS := $(SOURCES:%.tex=$(OUTPUT_DIR)/%.svg)

.PHONY: all clean

all: $(SVGS)

$(OUTPUT_DIR)/%.svg: %.tex truth-tree-style.tex
	mkdir -p $(BUILD_DIR) $(OUTPUT_DIR)
	latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=$(BUILD_DIR) $<
	pdftocairo -svg $(BUILD_DIR)/$*.pdf $@

clean:
	latexmk -C -outdir=$(BUILD_DIR)
