NAME = FormalLanguageConstrainedReachabilityLectureNotes
ENGINE = lualatex # Only `xelatex` or `lualatex` are allowed here

.PHONY: $(NAME).pdf clean dist-clean format

all: $(NAME).pdf

$(NAME).pdf:
	latexmk -$(ENGINE) -synctex=1 -interaction=nonstopmode -file-line-error -shell-escape $(NAME).tex

clean:
	latexmk -c $(NAME).tex

dist-clean:
	latexmk -C $(NAME).tex

# https://stackoverflow.com/a/12959694
# Make does not offer a recursive wildcard function, so here's one:
rwildcard=$(wildcard $1$2) $(foreach d,$(wildcard $1*),$(call rwildcard,$d/,$2))

FILES_TO_FORMAT := $(call rwildcard,./,*.tex) \
		   $(call rwildcard,./,*.cls) \
		   $(call rwildcard,./,*.bib)
#$(info $(FILES_TO_FORMAT))

format:
	$(foreach file, $(FILES_TO_FORMAT), latexindent -l -s -o=$(file) -m $(file);)
