SOURCES := practice-01.tex practice-02.tex truth-tree-operations.tex example-valid.tex example-invalid.tex \
	implication-chain.tex exponential-growth.tex translate-infer-valid.tex translate-infer-invalid.tex
OUTPUT_DIR := ../../images/G01
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
