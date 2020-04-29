all: collisions

.PHONY: collisions
collisions: prefix.txt prefix_64.txt
	md5collgen -p prefix.txt -o out1.bin out2.bin
	md5collgen -p prefix_64.txt -o out1_64.bin out2_64.bin

%.bin.dump: %.bin
	hexdump -v $< > $@

.PHONY: compare
compare: out1.bin.dump out2.bin.dump out1_64.bin.dump out2_64.bin.dump
	-diff out1.bin.dump out2.bin.dump
	-diff out1_64.bin.dump out2_64.bin.dump

.PHONY: clean
clean:
	rm -f *.bin *.dump
