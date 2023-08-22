.PHONY: builddir

all: builddir
	for pr in signal_processing vad;  do \
		$(MAKE) -C $$pr && cp $$pr/build/*.{h,lib} build; \
	done

builddir:
	mkdir -p build

clean:
	$(MAKE) -C signal_processing clean
	$(MAKE) -C vad clean
	rm -rf build
