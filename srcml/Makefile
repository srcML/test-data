EXT = .gz .bz2 .tar .cpio .zip .gz.bz2 .bz2.gz .tar.gz .tar.bz2 .tgz .tbz2 .zip.bz2 .zip.gz .cpio.gz .cpio.bz2
unit_targets = $(addprefix unit.xml, $(EXT))
emptyunit_targets = $(addprefix emptyunit.xml, $(EXT))
archive-single_targets = $(addprefix archive-single.xml, $(EXT))
archive-multi_targets = $(addprefix archive-multi.xml, $(EXT))
targets = $(unit_targets) $(emptyunit_targets) $(archive-single_targets) $(archive-multi_targets) 

all : $(targets)

emptyunit.xml :
	srcml --text="" --hash -l C++ --filename="empty.cpp" -o emptyunit.xml

# gz
%.xml.gz : %.xml
	gzip -k $<

%.xml.gz.bz2 : %.xml.gz
	bzip2 -k $<

# bz2
%.xml.bz2 : %.xml
	bzip2 -k $<

%.xml.bz2.gz : %.xml.bz2
	gzip -k --force $<

# tar
%.xml.tar : %.xml
	tar cf $@ $<

%.xml.tar.gz : %.xml.tar
	gzip -k --force $<

%.xml.tar.bz2 : %.xml.tar
	bzip2 -k $<

%.xml.tgz : %.xml.tar.gz
	cp $< $@

%.xml.tbz2 : %.xml.tar.bz2
	cp $< $@

# zip
%.xml.zip : %.xml
	zip $@ $<

%.xml.zip.bz2 : %.xml.zip
	bzip2 -k $<

%.xml.zip.gz : %.xml.zip
	gzip -k $<

# cpio
%.xml.cpio : %.xml
	ls $< | cpio -o > $@

%.xml.cpio.bz2 : %.xml.cpio
	bzip2 -k $<

%.xml.cpio.gz : %.xml.cpio
	gzip -k $<

.PHONY: clean
clean :
	rm -fR $(targets)
