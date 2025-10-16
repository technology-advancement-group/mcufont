# Path to the command-line utility program
MCUFONT = ../encoder/mcufont

# Names of fonts to process
FONTS = consolab15 \
	consola10 consola15 consola20 consola25 consola30 consola40 \
	cour13 cour14 \
	fixed_5x8 fixed_7x14 fixed_10x20 \
	verdana25

# Characters to include in the fonts ' '..'~'
CHARS = 20-126

all: $(FONTS:=.c) $(FONTS:=.dat) fonts.h

clean:
	rm -f $(FONTS:=.c) $(FONTS:=.dat)

fonts.h: $(FONTS:=.c)
	printf '$(foreach font,$(FONTS),\n#include "$(font).c")\n' > $@

%.c: %.dat $(MCUFONT)
	$(MCUFONT) rlefont_export $<

consolab15.dat: consolab.ttf
	$(MCUFONT) import_ttf $< 15
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola10.dat: consola.ttf
	$(MCUFONT) import_ttf $< 10
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola15.dat: consola.ttf
	$(MCUFONT) import_ttf $< 15
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola20.dat: consola.ttf
	$(MCUFONT) import_ttf $< 20
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola25.dat: consola.ttf
	$(MCUFONT) import_ttf $< 25
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola30.dat: consola.ttf
	$(MCUFONT) import_ttf $< 30
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

consola40.dat: consola.ttf
	$(MCUFONT) import_ttf $< 40
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

cour13.dat: cour.ttf
	$(MCUFONT) import_ttf $< 13
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

cour14.dat: cour.ttf
	$(MCUFONT) import_ttf $< 14
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

fixed_5x8.c: fixed_5x8.dat $(MCUFONT)
	$(MCUFONT) bwfont_export $<

verdana25.dat: verdana.ttf
	$(MCUFONT) import_ttf $< 25
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50

%.dat: %.bdf
	$(MCUFONT) import_bdf $<
	$(MCUFONT) filter $@ $(CHARS)
	$(MCUFONT) rlefont_optimize $@ 50
