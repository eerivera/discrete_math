SOURCES := practice-parse-tree.tex scope-example-1.tex scope-example-2.tex
OUTPUT_DIR := ../../images/F05
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
