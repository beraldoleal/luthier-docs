# Paths
FONTS_PATH = assets/fonts
STYLES_PATH = assets/styles
BUILD_PATH = build
LANGUAGES = fr en

# Default target builds everything
all: pdf html epub

# Loop over languages for each build target
pdf: $(foreach lang,$(LANGUAGES),pdf-$(lang))

html: $(foreach lang,$(LANGUAGES),html-$(lang))

epub: $(foreach lang,$(LANGUAGES),epub-$(lang))

# Clean target
clean:
	rm -rf $(BUILD_PATH)

# Per-language PDF, HTML, and EPUB builds
pdf-%:
	mkdir -p $(BUILD_PATH)
	asciidoctor-pdf -a pdf-fontsdir=$(FONTS_PATH) \
	                -a pdf-stylesdir=$(STYLES_PATH) \
	                -D $(BUILD_PATH) \
	                -o Book_$*.pdf \
	                $*/index.adoc

html-%:
	mkdir -p $(BUILD_PATH)
	asciidoctor -D $(BUILD_PATH) \
	            -o index_$*.html \
	            $*/index.adoc

epub-%:
	mkdir -p $(BUILD_PATH)
	asciidoctor-epub3 -D $(BUILD_PATH) \
	                  -o Book_$*.epub \
	                  $*/index.adoc
