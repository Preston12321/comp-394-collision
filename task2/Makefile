all: collision concat

.PHONY: collision
collision: prefix.txt
	md5collgen -p prefix.txt -o prefix1.bin prefix2.bin

.PHONY: concat
concat: prefix1.bin prefix2.bin suffix.txt
	cat prefix1.bin suffix.txt > complete1.bin
	cat prefix2.bin suffix.txt > complete2.bin

.PHONY: sum
sum: complete1.bin complete2.bin
	md5sum complete1.bin
	md5sum complete2.bin

.PHONY: clean
clean:
	rm -f *.bin
